---
title: "Run 2 Commands in Gnome App Launcher"
date: 2009-01-18
forum: General Help
---

### Post by angelkiller on 2009-01-18
Ok. I just got Folding@home installed and working on my Ubuntu box. Now I want a launcher on my Gnome panel. I know how to create the launcher but I'm confused on how I launch the application.

To run F@H, in the terminal, I put:
```
cd ~/folding
./fah6 -smp -verbosity
```

My first question is how do I get a launcher to run these commands? There is only one command space, I need to run two commands. Running:
```
~/folding/./fah6 -smp -verbosity 9
``` does not use the correct .cfg file. That command uses the .cfg file in my home directory, not the correct one in the /home/folding directory.

Second, what does the "./" mean? The application will not run correctly without it.

There's probably an elegant solution to do this that I don't know. Your help and advice is greatly appreciated!

---

### Post by oldos2er on 2009-01-18
You can combine two commands into one by using "&&" between them:

cd ~/folding && ./fah6 -smp -verbosity

 or write a simple script. The "./" tells bash to look for fah6 in the current directory.

---

### Post by unutbu on 2009-01-18
You could try this:
```
cd ~/folding && ./fah6 -smp -verbosity
```

The && means 'and'. First the "cd" command will be run, and if successful, the "./fah6" command will be run.

The "./" in front of fah6 is used to tell the shell where to look for the fah6 program. The period "./" means "look here in the current working directory". 

You can remove the "./" from the command if you add ~/folding to your PATH. Whenever a command is specified, the shell looks for the executable in each of the directories specified by the PATH environment variable.

See 
[http://ubuntuforums.org/showpost.php?p=5953944&postcount=2](http://ubuntuforums.org/showpost.php?p=5953944&postcount=2)
for instructions on how to set your PATH.

---

### Post by voxel on 2009-01-18
The ./ refers to the current working directory.

so two equivalent ways of running an application from the terminal are:
cd /path/to/program
./program_name

and

/path/to/program/program_name

in your case you could make the launcher command:
~/folding/fah6 -smp -verbosity

Hope that helps

---

### Post by angelkiller on 2009-01-19
Thanks for the replies. Everything everyone said makes sense.

```
cd ~/folding && ./fah6 -smp -verbosity 9
```This command works perfectly in the terminal. However, when run from the launcher, I get an error: "There was an error creating the child process for this terminal"

```
~/folding/fah6 -smp -verbosity 9
```This command launches F@H, but it uses the .cfg file in my home directory rather than the /home/folding directory. I get the same error as above when using this command in the launcher.


[list][*]Since neither command works in the launcher, could it be an issue with how F@H runs? :confused:  (ie F@H must be run from terminal only? I have no idea)
[*]I'm also confused as to how the second command won't work in terminal. Stanford's F@H setup guide is what told me to change to the ~/folding directory then run ./fah6. Maybe the "./" has some sort of significance?
[*][quote="unutbu"]The "./" in front of fah6 is used to tell the shell where to look for the fah6 program. The period "./" means "look here in the current working directory".[/quote]
Rather what? How is "cd ~/folding/fah6" different from "cd ~/folding" and then "./fah6". In other words, where *else* would the shell look for fah6 *other* than the working directory. So if I'm in a directory, and I give a command, wouldn't the shell look in that directory first?[/list]

Thanks in advance!

---

### Post by unutbu on 2009-01-19
Since you are getting this error: "There was an error creating the child process for this terminal", perhaps try
```

bash -c "cd ~/folding && ./fah6 -smp -verbosity 9"
```

as the command for the launcher. This will run a bash shell, and then run the command from within the bash shell. Maybe this will work, but I'm not sure.

Now, regarding your question, "Rather [than] what?": For a security reason, the current
directory is not searched by default for executables. Imagine if you were a system 
administrator and you cd into a malicious user's home directory. Suppose the malicious
user planted executables in his home directory with names like "ls", "cd", or whatever.
The malicious user hopes the administrator types one of these commands. If the 
current working directory was part of the PATH by default, the administrator might
unwittingly run an executable in the malicious user's home directory. 
To make it less likely that such a thing could happen, the PATH does not include the
current working directory. 

If you type 
```

echo $PATH 
```

you will see the list of directories that your shell searches for executables.

---

### Post by angelkiller on 2009-01-19
> **unutbu said:**
> Since you are getting this error: "There was an error creating the child process for this terminal", perhaps try
```

bash -c "cd ~/folding && ./fah6 -smp -verbosity 9"
```

as the command for the launcher. This will run a bash shell, and then run the command from within the bash shell. Maybe this will work, but I'm not sure.

Now, regarding your question, "Rather [than] what?": For a security reason, the current
directory is not searched by default for executables. Imagine if you were a system 
administrator and you cd into a malicious user's home directory. Suppose the malicious
user planted executables in his home directory with names like "ls", "cd", or whatever.
The malicious user hopes the administrator types one of these commands. If the 
current working directory was part of the PATH by default, the administrator might
unwittingly run an executable in the malicious user's home directory. 
To make it less likely that such a thing could happen, the PATH does not include the
current working directory. 
Ok, that command works! Awesome! :)  Can I ask what is bash?

And I get what you're saying about the directory and executables thing. So by default it checks the directories listed in the PATH file and the "./" makes it search in the current directory. Makes sense now.

Thanks again.

---

### Post by unutbu on 2009-01-19
Hey, what do you know? It worked! :)

bash is the program that runs by default when you open up a terminal. It is also called a "shell". When you type "cd", or "ls", it is really the shell that is interpreting this command (in the case of "cd") or running the executable (in the case of "/bin/ls"). 

sh (also known as dash) is another shell, as is zsh, tsh, csh, tcsh, ash, ... and the list goes on.

Apparently, the launcher runs executables directly -- not through a shell. This is related to why you got an error. 
Maybe the launcher does not know how to interpret the "cd" command, because "cd" is not an executable. It is only a command understood within a shell. The same is true of "&&".

bash is itself an executable, which is perhaps why wrapping the command inside of bash worked.

bash -c "STRING" tells bash to interpret STRING as commands.

---

### Post by angelkiller on 2009-01-19
Cool, thanks. What you said makes sense. Thanks for your and everyone else's help!

---

### Post by joopbraak on 2010-12-07
Thank you. I wish all Linux nerds (I'm not saying you are one! ;-) ) were so friendly.

---

