---
title: "Executing Binary Files does nothing"
date: 2006-07-04
forum: Desktop Environments
---

### Post by Disstress on 2006-07-04
I try to execute binary files and nothing happens. 
So I open up terminal and /cd to the directory where the binary is and it tells me:

bash: bash:: command not found

So then I try to do 'bash <filename> and I get:

bash: <filename>: command not found

I made sure that bash was installed, and then I opened up Anjuta and made a simple 'Hello World' script in C++ to see if I could get it to run:

$ bash hello
hello: hello: cannot execute binary file
$ hello
bash: hello: command not found
$ hello.bin
bash: hello.bin: command not found

So I am stuck, I installed XFCE and KDE from the repos today, I am going to try to uninstall them and see if this is where I went wrong *omgsh just thought about all the window manager comments bound to come*

Any ideas are greatly appreciated!

---

### Post by DoktorSeven on 2006-07-04
Only BASH script files can be executed with the 'bash filename' command.

To run an executable file:

make sure it's executable: **chmod +x filename**
run it using either the full path to the directory it's in or ./ (meaning current directory) if you're in the same directory it's in: **./filename** or **/full/path/to/filename**

(replace **filename** with the actual program name, of course, and the path to the actual path it's in, like **/usr/bin/**)

You can't execute a program in the current directory by simply typing its name because your PATH (which BASH uses to find all executable programs) doesn't contain the current directory, thus using ./ to specify "look in the current directory for this program.

---

### Post by Arisna on 2006-07-05
Also note that the PATH does not include the current directory ( "." ) by default because of the risk of someone unwittingly having, for example, an executable called "ls" stored somewhere that deletes the entire contents of the home folder of any user who runs it.

---

### Post by Disstress on 2006-07-05
Thank you for the replies, I learn more and more every day.

---

