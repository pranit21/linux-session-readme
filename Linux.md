# First command
```bash
ls -l
```

```bash
ls -l /home
```

### To print which shell you are using, type
```bash
echo $SHELL
```

# Basic Navigation
## pwd
`pwd` command which stands for Print Working Directory. It tells you what your current working directory is.

```bash
pwd
```

## What's in our current location?
```bash
ls
```

Where `pwd` runs by itself with no arguments, `ls` is more powerful than that. We can do more with `ls` command by specifying its options. Below is the general syntax for `ls` command.

> `ls` [options] [location]

Try below commands to explore more about `ls`:
```bash
$ ls -l
drwx------  4 pranit  staff   128 Sep 29 11:03 Applications
drwx------  3 pranit  staff    96 Sep 29 10:40 Desktop
-rw-r--r--  1 pranit  staff   683 Oct  7 11:02 Linux.md
```

> Note: Don't use **$** while typing command. It is just used for reference to type command in terminal.

Let's break it down:\
When we ran `ls` with `-l`, it indicates we are going to do a long listing.
1. First character indicates whether it is a normal file (-) or directory (d).
2. The next 9 characters are permissions for the file or directory.
3. The next field is the number of blocks.
4. The next field is the owner of the file or directory (pranit in this case).
5. The next field is the group the file or directory belongs to (staff in this case).
6. Following is the size of the file.
7. Next is the time at which the file or directory is modified.
8. Lastly, we have file or directory name.


```bash
$ ls -l /home   # will list down all files or directories from /home directory
```

## Absolute & Relative Paths
There are 2 types of paths we can use, **absolute** and **relative**. Whenever we refer to a file or directory we are using one of these paths.

To begin with, we have to understand that the file system under linux is a hierarchical structure. At the very top of the structure is what's called the **root** directory. It is denoted by a single slash (/).

Absolute paths specify a location (file or directory) in relation to the **root** directory. You can identify them easily as they always begin with a forward slash (/).

Relative paths specify a location (file or directory) in relation to where we currently are in the system. They will not begin with a slash.

e.g. try below commands and observe the output
```bash
$ pwd           # print working directory path from root
$ ls /home      # absolute path
$ ls Desktop    # relative path
```

## More on Paths
You'll find that paths in Linux can be achieved in several different ways. Here are some ways:
- **~ (tilde)** - This is a shortcut for your home directory. e.g., if your home directory is /home/pranit then you could refer to the directory Desktop with the path /home/pranit/Desktop or ~/Desktop
- **. (dot)** - This is a reference to your current directory. e.g. in the example above we referred to **Desktop** with a relative path. It could also be written as **./Desktop** (Normally this extra bit is not required but in later sections we will see where it comes in handy).
- **.. (dotdot)** - This is a reference to the parent directory. You can use this several times in a path to keep going up the hierarchy. e.g. if you were in the path /home/pranit you could run the command ls **../../** and this would do a listing of the root directory.

Try following commands & observe the output:
```bash
$ ls ~/Desktop
$ ls ./Desktop
$ ls /home/pranit/Desktop
$ ls .
$ ls ../
$ ls ../../
$ ls /
```

## Let's move around a bit
In order to move around in the system we use a command called `cd` which stands for Change Directory. It's syntax is as follows:
> `cd` [location]

> **Tip:** If you run `cd` command without any arguments, then it will always take you back to your home directory.

Try below commands to see how `cd` command works:
```bash
$ cd
$ cd Desktop
$ ls
$ cd /
$ cd ~/Desktop
$ pwd
$ cd ../../
$ pwd
```

> **Tip:** Typing out these paths can be tedious. We are human beings and we are prone to make mistakes while typing a path name. The command line has nice little help in this respect. It's called **Tab Completion**.
> 
> When you start typing a path (anywhere on the command line, you're not just limited to certain commands) you may hit the `Tab` key on your keyboard at any time which will invoke an auto complete action. If nothing happens then that means there are several possibilities. If you hit `Tab` again it will show you those possibilities. You may then continue typing and hit `Tab` again and it will again try to auto complete for you.


# About Files
- Everything in linux is file, even directory is a file.
- Linux is extensionless system.
  - A file extension is normally a set of 2 - 4 characters after a full stop at the end of a file, which denotes what type of file it is. For e.g., file.txt, file.png, file.exe, etc.
  - In other systems such as Windows the extension is important and the system uses it to determine what type of file it is.
  - Under Linux the system actually ignores the extension and looks inside the file to determine what type of file it is.
  - So for instance I could have a file *dog.png* which is a picture of *dog*. I could rename the file to *dog.txt* or just *dog* and Linux would still happily treat the file as an image file.
  - There is a command in linux called `file` which we can use to find out the type of file. Syntax - `file [path]`
- Linux is case-sensitive.
- Spaces in names are perfectly valid, but you need to be little careful with them. As you would remember, a space on the command line is how we seperate items. If we wanted to move into a directory called **My Pictures** for example the following would not work. `$ cd My Pictures`. There are 2 approaches to resolve this issue.
  - First approach is to wrap your file or directory name in quotes like - `$ cd "My Pictures"`
  - Another method is to use escape character backslash (\\). This will nullify the special meaning of next character. `$ cd My\ Pictures`
- Files or directories can be hidden by just specifying . (dot) before the file or directory name. e.g. .hidden
  - By default hidden files or directories are not shown when you use `ls` command.
  - If you want to see hidden files, then you can use `-a` option along with `ls`. e.g. `ls -a`

# Manual Pages
You can get help for any command by using `man` command which stands for Manual.
Let's say we want to see the help of `ls` command, then use following command:
```bash
$ man ls
```
This will display manual for `ls` command page by page. You can navigate through every page pressing `spacebar` key. If you want to quit the manual, press `q` key.

# File Manipulation
## Making a directory
Creating a directory is pretty easy. The command we are after is `mkdir` which stands for Make Directory.
> `mkdir [options] <Directory>`

```bash
$ mkdir linux_directory     # this will create a directory named linux_directory inside current working directory
$ ls
$ mkdir -p linux_directory/parent1/parent2  # -p tells mkdir to make parent directories as needed
```

## Removing a directory
Removing or deleting a directory is easy too. One thing to note, however, is that there is no undo when it comes to the command line on Linux. Just be careful with what you do. The command to remove a directory is `rmdir`, short for Remove Directory.
> `rmdir [options] <Directory>`

Two things to note. Firstly, `rmdir` supports -p option similar to `mkdir`. Secondly, a directory must be empty before it may be removed.

```bash
$ rmdir -p linux_directory/parent1/parent2
$ ls
```

## Creating a blank file
There is the basic command to create a blank file - `touch`.
> `touch [options] <filename>`

For e.g.
```bash
$ touch file.txt
$ ls
```
We can also use paths in filename like - `touch ../file.txt`. This will create a file named **file.txt** in the parent directory of current working directory.

## Copying a file or directory
There are many reasons why we may want to make a duplicate of a file or directory. Often before changing something, we may wish to create a duplicate so that if something goes wrong we can easily revert back to the original. The command we use for this is `cp` which stands for Copy.
> `cp [options] <source> <destination>`

For e.g.
```bash
$ cp file.txt filecopy.txt
$ ls
```

We can use `-r` option, which stands for recursive. This can be used to copy files & directories from the specified source.

## Moving a file or directory
To move a file we use the command `mv` which is short for Move. It operates in a similar way to `cp`. One slight advantage is that we can move directories without having to provide the `-r` option.
> `mv [options] <source> <destination>`

For e.g.
```bash
$ mkdir backups
$ mv file.txt backups/
$ ls backups/
```

## Renaming files or directories
Normally `mv` will be used to move a file or directory into a new directory. But it can also be used to rename a file or directory by changing the destination file or directory name.
For e.g.
```bash
$ mv file.txt file1.txt
$ ls
```

## Removing a file and non-empty directories
The command to remove or delete a file is `rm` which stands for Remove.
> `rm [options] <file>`

For e.g.
```bash
$ rm file1.txt
$ ls
```

To remove non-empty directories, you can specify `-r` option similar to `cp` which stands for recursive. It will recursively delete all the files & directories contained within it.
For e.g.
```bash
$ rmdir backups
rmdir: failed to remove 'backups': Directory not empty
$ rm backups
rm: cannot remove 'backups': Is a directory
$ rm -r backups
$ ls
```

# Vi Text Editor
Master the Vi text editor and learn how to make complex edits on your files with less time and effort. Vi is a very powerful tool. In this section we will not cover everything that Vi can do, but we will learn the basics of what Vi can do.

Vi is a command line text editor. As you would be quite aware now, the command line is quite a different environment to your GUI. It's a single window with text input and output only. Vi has been designed to work within these limitations and many would argue, is actually quite powerful as a result. Vi is intended as a plain text editor. Everything in Vi is done via the keyboard.

There are two modes in Vi. **Insert** (or Input) mode and **Edit** mode. In input mode, you may input or enter content into the file. In edit mode, you can move around the file, perform actions such as deleting, copying, search and replace, saving etc.

When we run vi we normally issue it with a single command line argument which is the file you would like to edit.
> `vi <file>`

Let's go and edit your first file:
```bash
$ vi myfile
```
When you run this command it opens up the file. If the file does not exist then it will create it for you then open it up. Once you enter vi it will look something like this:

```bash
~
~
~
~
"myfile" [New]
```
You always start off in **edit** mode so the first thing we are going to do is switch to **insert** mode by pressing `i`. You can tell when you are in **insert** mode by looking at the bottom left corner.

```bash
~
~
~
~
-- INSERT --
```
Now type in a few lines of text and press `Esc` which will take you back to **edit** mode.

## Saving and Exiting
There are a few ways to go about doing this. They all do essentially the same thing so pick whichever way you prefer. For all of these, make sure you are in **edit** mode first.
- `ZZ` (Note: capitals) - Save and exit
- `:q!` - discard all changes, since the last save, and exit
- `:w` - save file but don't exit
- `:wq` - again, save and exit

Most commands within vi are executed as soon as you press a sequence of keys. Any command beginning with a colon (:) requires you to hit `<enter>` to complete the command.

Save and exit the file you currently have open.

## Other ways to view files
vi allows us to edit files. If we wanted, we could use it to view files as well, but there are two other commands which are a bit more convenient for that purpose. The first one is `cat` which actually stands for concatenate. It's main purpose is to join files together but in it's most basic form it is useful for just viewing files.
> `cat <file>`

For e.g.
```bash
$ cat myfile
```

This command is nice when we have a small file to view but if the file is large then most of the content will fly across the screen and we'll only see the last page of content. For larger files there is a better suited command which is `less`.
> `less <file>`

`less` allows you to move up and down within a file using the arrow keys. You may go forward a whole page using the `SpaceBar` or back a page by pressing `b`. When you are done you can press `q` for quit.

# Permissions
Permissions specify what a particular person may or may not do with respect to a file or directory. As such, permissions are important in creating a secure environment. Luckily, permissions in a Linux system are quite easy to work with.

Linux permissions dictate 3 things you may do with a file, read, write and execute. They are referred to in Linux by a single letter each.
- **r** read - you may view the contents of the file.
- **w** write - you may change the contents of the file.
- **x** execute - you may execute or run the file if it is a program or script.

For every file we define 3 sets of people for whom we may specify permissions.
- **owner** - a single person who owns the file. (typically the person who created the file but ownership may be granted to some one else by certain users)
- **group** - every file belongs to a single group.
- **others** - everyone else who is not in the group or the owner.

Three persmissions and three groups of people. That's about all there is to permissions really. Now let's see how we can view and change them.

## View Permissions
To view permissions for a file we use the long listing option for the command `ls`.
> `ls -l [path]`

For e.g.
```bash
$ mkdir backups
$ cd backups
$ touch myfile.txt
$ ls -l
-rw-r--r--  1 pranit  staff  13 Oct  7 13:46 myfile.txt
```

In the above example the first 10 characters of the output are what we look at to identify permissions.
- The first character identifies the file type. If it is a **-** (dash) then it is a normal file. If it is a **d** then it is a directory.
- The following 3 characters represent the permissions for the **owner**. A letter represents the presence of a permission and a dash (-) represents the absence of a permission. In this example the owner has read and write permissions.
- The following 3 characters represent the permissions for the **group**. In this example the group has the ability to read but not write or execute. Note that the order of permissions is always read, then write then execute.
- Finally the last 3 characters represent the permissions for **others** (or everyone else). In this example they have the read permission and nothing else.

## Change Permissions
To change permissions on a file or directory we use a command called `chmod`. It stands for change file mode bits which is a bit of a mouthfull but think of the mode bits as the permission indicators.
> `chmod [permissions] [path]`

`chmod` has permission arguments that are made up of 3 components
- Who are we changing the permission for? [ugoa] - user (or owner), group, others, all
- Are we granting or revoking the permission - indicated with either a plus ( + ) or minus ( - )
- Which permission are we setting? - read ( r ), write ( w ) or execute ( x )

The following examples will make their usage clearer.

```bash
$ ls -l
-rw-r--r--  1 pranit  staff  13 Oct  7 13:46 myfile.txt

$ chmod g+x myfile.txt      # add execute permission for group
$ ls -l myfile.txt
-rw-r-xr--  1 pranit  staff  13 Oct  7 13:46 myfile.txt

$ chmod u-w myfile.txt      # remove write permission for owner
$ ls -l myfile.txt
-r--r-xr--  1 pranit  staff  13 Oct  7 13:46 myfile.txt
```

Don't want to assign permissions individually? We can assign multiple permissions at once.

```bash
$ ls -l
-r--r-xr--  1 pranit  staff  13 Oct  7 13:46 myfile.txt

$ chmod g+wx myfile.txt     # add write & execute permission for group
$ ls -l myfile.txt
-r--rwxr--  1 pranit  staff  13 Oct  7 13:46 myfile.txt

$ chmod go-x myfile.txt     # remove execute permission for group & others
$ ls -l myfile.txt
-r--rw-r--  1 pranit  staff  13 Oct  7 13:46 myfile.txt
```

## Setting Permissions Shorthand
The method outlined above is not too hard for setting permissions but it can be a little tedious if we have a specific set of permissions we would like to apply regularly to certain files. Luckily, there is a shorthand way to specify permissions that makes this easy.

To understand how this shorthand method works we first need a little background in number systems. Our original number system is decimal which has 10 symbols (0-9). Another number system is octal which contains 8 symbols (0-7). Now it just so happens that with 3 permissions and each being on or off, we have 8 possible combinations ($2^3$). Now we can also represent our numbers using binary which only has 2 symbols (0 and 1). The mapping of octal to binary is in the table below.

| Octal | Binary |
| - | ----- |
|   | r w x |
| 0 | 0 0 0 |
| 1 | 0 0 1 |
| 2 | 0 1 0 |
| 3 | 0 1 1 |
| 4 | 1 0 0 |
| 5 | 1 0 1 |
| 6 | 1 1 0 |
| 7 | 1 1 1 |

We have 3 bits and we also have 3 permissions. If you think of 1 as representing on and 0 as off then a single octal number may be used to represent a set of permissions for a set of people. Three numbers and we can specify permissions for the user, group and others. Let's see some examples.

```bash
$ ls -l
-rw-r----x  1 pranit  staff  13 Oct  7 13:46 myfile.txt

$ chmod 751 myfile.txt
$ ls -l myfile.txt
-rwxr-x--x  1 pranit  staff  13 Oct  7 13:46 myfile.txt

$ chmod 240 myfile.txt
$ ls -l myfile.txt
--w-r-----  1 pranit  staff  13 Oct  7 13:46 myfile.txt
```

People often remember commonly used number sequences for different types of files and find this method quite convenient. For example **755** or **750** are commonly used for scripts.

## Permissions for Directories
The same series of permissions may be used for directories but they have a slightly different behaviour.
- **r** - you have the ability to read the contents of the directory (i.e. do an `ls`)
- **w** - you have the ability to write into the directory (i.e. create files and directories)
- **x** - you have the ability to enter that directory (i.e. `cd`)

## The root user
On a Linux system, there are only 2 people usually who may change the permissions of a file or directory. The **owner** of the file or directory and the **root** user. The **root** user is a superuser who is allowed to do anything and everything on the system.

# Filters
A filter, in the context of the Linux command line, is a program that accepts textual data and then transforms it in a particular way. Filters are a way to take raw data, either produced by another program, or stored in a file, and manipulate it to be displayed in a way more suited to what we are after.

These filters often have various command line options that will modify their behaviour so it is always good to check out the man page for a filter to see what is available.

Let's create one file named **sampledata.txt** `vi sampledata.txt`, press `i` and add following content into it.
```
Akshay apples 20
Ram oranges 25
Shyam mangoes 30
Vijay grapes 15
Akshay mangoes 10
Vijay apples 20
Ajay apples 35
```
Press `Esc` and type `:wq` and hit `<enter>`. This will create the file with above content into it.

`cat` command will print out the entire content of the file.

```bash
$ cat sampledata.txt
Akshay apples 20
Ram oranges 25
Shyam mangoes 30
Vijay grapes 15
Akshay mangoes 10
Vijay apples 20
Ajay apples 35
```

`head` command is used to print 1st few lines of the file. By default, it prints first 10 lines. We can specify the number of lines afte `head` command.
> `head [-number of lines to print] [path]`

```bash
$ head -5 sampledata.txt
Akshay apples 20
Ram oranges 25
Shyam mangoes 30
Vijay grapes 15
Akshay mangoes 10
```

`tail` command is used to print last few lines of the file. By default, it prints last 10 lines. We can specify the number of lines afte `tail` command.
> `tail [-number of lines to print] [path]`

```bash
$ tail -5 sampledata.txt
Shyam mangoes 30
Vijay grapes 15
Akshay mangoes 10
Vijay apples 20
Ajay apples 35
```

`sort` will sort it's input. By default it will sort alphabetically but there are many options available to modify the sorting mechanism.
> `sort [-options] [path]`

```bash
$ sort sampledata.txt
Ajay apples 35
Akshay apples 20
Akshay mangoes 10
Ram oranges 25
Shyam mangoes 30
Vijay apples 20
Vijay grapes 15
```

## Grep command
`grep` is a program which will search a given set of data and print every line which contains a given pattern.
> `grep [command line options] <pattern> [path]`

In the above data that we entered, let's say we wished to identify every line which contained the string **mangoes**
```bash
$ grep 'mangoes' sampledata.txt
Shyam mangoes 30
Akshay mangoes 10
```

The basic behaviour of `grep` is that it will print the entire line for every line which contains a string of characters matching the given pattern. This is important to note, we are not searching for a word but a string of characters.

Sometimes we want to know not only which lines matched but their line number as well.
```bash
$ grep -n 'mangoes' sampledata.txt
3:Shyam mangoes 30
5:Akshay mangoes 10
```

Or maybe we are not interested in seeing the matched lines but wish to know how many lines did match.
```bash
$ grep -c 'mangoes' sampledata.txt
2
```

# Process Management
Linux, like most modern OS's is a multitasking operating system. This means that many processes can be running at the same time. As well as the processes we are running, there may be other users on the system also running stuff and the OS itself will usually also be running various processes which it uses to manage everything in general. If we would like to get a snapshot of what is currently happening on the system we may use a program called `top`.
> `top`

```bash
$ top
Processes: 429 total, 2 running, 427 sleeping, 3555 threads                                     14:45:52
Load Avg: 2.63, 1.86, 1.59  CPU usage: 1.28% user, 2.9% sys, 96.62% idle
SharedLibs: 287M resident, 68M data, 17M linkedit.
MemRegions: 723204 total, 1383M resident, 86M private, 1227M shared.
PhysMem: 7533M used (1350M wired), 95M unused.
VM: 223T vsize, 3831M framework vsize, 8692557(0) swapins, 11125757(0) swapouts.
Networks: packets: 21718400/29G in, 11086708/16G out. Disks: 19363439/430G read, 14813411/434G written.

PID    COMMAND      %CPU TIME     #TH   #WQ  #PORT MEM    PURG   CMPRS  PGRP  PPID  STATE
12132  top          6.2  00:01.22 1/1   0    29    6737K  0B     0B     12132 7929  running
0      kernel_task  4.4  04:25:59 467/8 0    0     19M-   0B     0B     0     0     running
166    WindowServer 3.7  04:51:03 19    6    2585- 691M+  256K+  112M   166   1     sleeping
54994  Google Chrom 1.0  44:27.87 46    3    1985  692M-  0B     528M-  54994 1     sleeping
552
```

You can come out of `top` command by pressing `q`.

`top` will give you a realtime view of the system and only show the number of processes which will fit on the screen. Another program to look at processes is called `ps` which stands for processes. In it's normal usage it will show you just the processes running in your current terminal (which is usually not very much). If we add the argument `aux` then it will show a complete system view which is a bit more helpful.
> `ps [aux]`

```bash
$ ps
  PID TTY           TIME CMD
55194 ttys000    0:00.09 /bin/zsh -il
68434 ttys001    0:00.05 /bin/zsh -il
68137 ttys002    0:00.05 /bin/zsh -il
80447 ttys003    0:00.07 /bin/zsh -il
67765 ttys004    0:00.05 -zsh
67899 ttys004    0:28.43 mongosh
67851 ttys005    0:00.05 /bin/zsh -il
 7929 ttys006    0:00.32 -zsh

$ ps aux
```

It does give quite a bit of output so people usually pipe the output to `grep` to filter out just the data they are after.

# Piping
To send data from one program to another, we use piping. The operator used is pipe ( | ). What this operator does is feed the output from the program on the left as input to the program on the right.

```bash
$ ls
AngularProjects	GitProjects	Movies		ReactProjects	demo
Applications	ITVedant	Music		Sites
Desktop		JavaPrograms	NodeJSProjects	Spring
$ ls | head -3
AngularProjects
Applications
Desktop
```

```bash
$ ps aux | grep 'chrome'
pranit           55243   0.0  0.0 408107536   1408   ??  S    Mon05PM   0:00.17 /Applications/Google Chrome.app/Contents/Frameworks/Google Chrome Framework.framework/Versions/105.0.5195.125/Helpers/chrome_crashpad_handler --monitor-self-annotation=ptype=crashpad-handler --database=/Users/pranit/Library/Application Support/Google/Chrome/Crashpad --metrics-dir=/Users/pranit/Library/Application Support/Google/Chrome --url=https://clients2.google.com/cr/report --annotation=channel= --annotation=plat=OS X --annotation=prod=Chrome_Mac --annotation=ver=105.0.5195.125 --handshake-fd=5
```

# Killing a process
It doesn't happen often, but when a program crashes, it can be quite annoying. Let's say we've got our browser running and all of a sudden it locks up. You try and close the window but nothing happens, it has become completely unresponsive. No worries, we can easily kill Chrome and then reopen it. To start off we need to identify the process id.

```bash
$ ps aux | grep 'chrome'
pranit           55243   0.0  0.0 408107536   1408   ??  S    Mon05PM   0:00.17 /Applications/Google Chrome.app/Contents/Frameworks/Google Chrome Framework.framework/Versions/105.0.5195.125/Helpers/chrome_crashpad_handler --monitor-self-annotation=ptype=crashpad-handler --database=/Users/pranit/Library/Application Support/Google/Chrome/Crashpad --metrics-dir=/Users/pranit/Library/Application Support/Google/Chrome --url=https://clients2.google.com/cr/report --annotation=channel= --annotation=plat=OS X --annotation=prod=Chrome_Mac --annotation=ver=105.0.5195.125 --handshake-fd=5
```

It is the number next to the owner of the process that is the PID (Process ID). We will use this to identify which process to kill. To do so we use a program which is appropriately called `kill`.
> `kill [signal] <PID>`

```bash
$ kill 55243
$ ps aux | grep 'chrome'
```
