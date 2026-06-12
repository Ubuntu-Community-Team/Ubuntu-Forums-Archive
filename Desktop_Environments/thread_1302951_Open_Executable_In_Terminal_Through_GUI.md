---
title: "Open Executable In Terminal Through GUI?"
date: 2009-10-27
forum: Desktop Environments
---

### Post by Ring-Ding on 2009-10-27
Hey, I was wondering if there was some way I could configure my Ubuntu so that when I double click or right click on an executable and have it automatically open and run in terminal, rather than having to open up terminal, navigate to the directory, then open it from there.

It seems silly that when I already navigated to the directory through the GUI that I should have to then do it again through terminal.

I think in windows this was called a shell extension and I think there was a way to add your own shell extensions (although I never figured out how to do it).

Thanks

---

### Post by kerry_s on 2009-10-27
did you even try it? if you click on a executable it gives you that very choice.

also if you install nautilus-open-terminal, you'll have a right click open terminal here.

---

### Post by yknivag on 2009-10-27
You should be able to make a clickable icon to do this without the typing by right clicking the desktop, selecting "Create Launcher..." and type the below in the "Command" box.

```
gnome-terminal myscript.sh
```

---

### Post by Ring-Ding on 2009-10-27
> **kerry_s said:**
> did you even try it? if you click on a executable it gives you that very choice.

also if you install nautilus-open-terminal, you'll have a right click open terminal here.

Uh, yeah I tried it, the reason I posted this is because I tried it and it didn't work.

The executables I'm trying to open have no extensions (maybe that's why I'm having this problem) because I compiled them myself and wasn't sure what the file extension for an executable file for linux is (I assumed there was no extension).

I double click on the executable and nothing happens. All I want is to be able to open the executable through my GUI and have it open in a terminal, rather than having to open a new terminal, navigate to the directory, and then open it.


edit:

I opened up /bin and was browsing through the native executables in that folder and it looks like some of the executables you can double click on and nothing happens (like with my exe) and some of them you double click on and it brings up a launch dialog (which is what I want with mine).

It seems like its something that depends on the exe file. How do I get mine to do that too?

I wonder if its a flag on the g++ compiler....


edit:

Just now I tried right clicking on it, then selecting open with->open with other application. Then in the open with dialog box that comes up theres an option at the bottom: use a custom command. I opened that then put in gnome-terminal then hit open. Well, it opened a terminal, but it didn't run my executable in it.

---

### Post by yknivag on 2009-10-28
There is no such thing as a "file extension" in Linux.  Whether or not a file can be executed is determined by the permissions.  Try right-clicking your script and then check that "Allow executing as a program" is ticked.

Once this is correct, check that you can run the file directly in the terminal. How you do this depends on exactly where it is saved, but if for example it is on the desktop then you would type:

```

cd ~/Desktop
./myscriptname

```

Does it execute here? And do what you want it to?

---

### Post by Ring-Ding on 2009-10-29
> **yknivag said:**
> There is no such thing as a "file extension" in Linux.  Whether or not a file can be executed is determined by the permissions.  Try right-clicking your script and then check that "Allow executing as a program" is ticked.

Once this is correct, check that you can run the file directly in the terminal. How you do this depends on exactly where it is saved, but if for example it is on the desktop then you would type:

```

cd ~/Desktop
./myscriptname

```Does it execute here? And do what you want it to?

My executable is a terminal application and thus runs in the terminal. I can open it fine through the terminal, I was just wondering if there was a way to automatically open a new terminal and run it in the terminal through the GUI (such as by double clicking or right clicking on the executable). Double clicking on my executable for me does nothing.

---

### Post by epicskillz on 2011-10-13
I have this exact same problem. 

With my Fortran compiler, all I had to do to install it was to double click it, and it went up in a separate terminal window.

But my program, which I know runs fine if i manually open a terminal, go to its dierectory and type ./<appname> - does NOT do anything if i double click it.

---

### Post by Morbius1 on 2011-10-13
I took Fortran in school longer ago than you have been alive I suspect so don't ask me any Fortran questions because that information is gone ;)

I would think that you would either have to change your application to specify that it open up in a terminal or create a launcher:

Right click the desktop > Create Launcher

In the command box:
```
gnome-terminal -x bash -c "/path/to/executable; bash"
```

---

### Post by crdlb on 2011-10-13
If you're going to create a launcher, the best way is to set the type to 'Application in Terminal', and set the command normally.

---

### Post by Morbius1 on 2011-10-13
I guess it depends on what the application is doing.

If I create a launcher using "Application in Terminal" with the command "ls -al /home" it executes that command and closes the terminal in less than a second.

If instead I run it as an "Application" with the command 
```
gnome-terminal -x bash -c "ls -al /home; bash"
```, it will open the terminal, run the command, and wait for me to close the terminal.

---

### Post by crdlb on 2011-10-13
> **Morbius1 said:**
> If I create a launcher using "Application in Terminal" with the command "ls -al /home" it executes that command and closes the terminal in less than a second.

That is true, but I don't consider 'ls' an application. To me, a terminal application is something like mc or top (or a GUI application that prints debugging info to the terminal). It looks like you could still use 'sh -c "ls; exec $SHELL"' with 'Application in Terminal' though. (The 'exec' is to avoid nested shells)

---

