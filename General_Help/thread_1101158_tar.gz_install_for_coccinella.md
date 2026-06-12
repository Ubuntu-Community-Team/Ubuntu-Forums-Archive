---
title: "tar.gz install for coccinella"
date: 2009-03-20
forum: General Help
---

### Post by Simpotico on 2009-03-20
Could anyone help me install Coccinella instant messaging client with built-in whiteboard? I have it saved as a .tar.gz file on my desktop right now. But I'm a bit of a rock when it comes to things like this and, I've been drinking... So, if you could explain it to me as if you were giving me directions to the bathroom so that I don't upchuck on your carpet, that would be great.

Thanks

[http://thecoccinella.org/](http://thecoccinella.org/)

---

### Post by mb_webguy on 2009-03-20
As far as I can tell, there's no installation required.  But since you're drunk, I'll break it down for you.

1) [Download the program]("http://prdownloads.sourceforge.net/coccinella/Coccinella-0.96.12Linux-x86.tar.gz") from that site, and extract the archive to your home directory.

2) Open the terminal, and type "cd Coccinella-0.96.12Linux-x86".  Since you're drunk, you probably want to just hit Tab after typeing "cd Co" to let it autocomplete for you.

3) Inside this directory is a file called Coccinella-0.96.12.bin, which is the program.  Make this file executable with the command "chmod +x Coccinella-0.96.12.bin".  Again, you'll probably want to use Tab to autcomplete it for you.

4) Run the program with the command "./Coccinella-0.96.12.bin".  

To make it easier on you, you'll probably want to create a "bin" folder in your home directory, move this file to that folder, create a symlink in that folder with the command "ln -s ~/bin/Coccinella-0.96.12.bin cocc".  No you can run the program by typing "cocc" in the terminal.  You could also add a launcher for the program in your Applications menu.  You might want to wait until you're sober to do this stuff, though.

---

### Post by Simpotico on 2009-03-20
Aaawwwwwwwwwwwwww, man. I'm feeling nauseated...

I've got the extraction part down but how do I "archive" it to my "home directory?"

Oh nooo, the room's starting to spin a little bit...

---

### Post by mb_webguy on 2009-03-20
Hrm... Maybe you ought to wait until you're sober.

When you click the link to download the file, select "Open with Archive Manager".

Now click the big "Extract" button at the top.  Now click the little "Extract" button in the bottom-right corner.  Now you've extracted the archive to your home directory. 

Now go back to my first post and start with step #2.  And make sure you read everything twice.  If it says something different the second time around, go take a nap for a few hours, drink some orange juice and possibly some coffee, and then come back and try again, ok? ;)

---

### Post by Simpotico on 2009-03-20
Thanks for your patience with me. I was able to extract it in the beginning but to my desktop. I'm pretty sure I now have it in my "home directory/folder" because it's the master file folder with the little house on it. If there was ever a folder that was screaming out that it was my home folder, that's the one. And hey, look at that, when I leave my mouse cursor over it, it even pops up with a little window that says, "Home Folder." That's pretty sweet.

Okay, now since I'm still functioning and I went ahead and cracked another cold one to help settle my stomach; I went ahead and copied and pasted the command line that you gave me, cd Coccinella-0.96.12Linux-x86, into the terminal and this is what it spit back at me in response and with no effect:

myhomefoldername@myhomefoldername-laptop:~/Coccinella-0.96.12Linux-x86$ 

What gives? BTW, I'm more of a rock then drunk. And I function better when I'm a little buzzed, lol.

---

### Post by mb_webguy on 2009-03-20
> **Simpotico said:**
> Okay, now since I'm still functioning and I went ahead and cracked another cold one to help settle my stomach; I went ahead and copied and pasted the command line that you gave me, cd Coccinella-0.96.12Linux-x86, into the terminal and this is what it spit back at me in response and with no effect:

myhomefoldername@myhomefoldername-laptop:~/Coccinella-0.96.12Linux-x86$ 

What gives? BTW, I'm more of a rock then drunk. And I function better when I'm a little buzzed, lol.

Hehe...  Ok, now you've completed step #2.  You're in the right folder, which you can tell by the bit between the ":" and the "$".  The tilda ("~") is shorthand for your home directory.

Now move right along to step #3.  You won't get any feedback if you enter the command correctly, but you'll probably get an error message if you don't do it correctly.

---

### Post by Simpotico on 2009-03-20
No, luck. I'm even doing using the cut and paste method just to make sure that I'm screwing a code up but this is all that I get:

myhomefoldername@myhomefoldername-laptop:~$ cd Coccinella-0.96.12Linux-x86
myhomefoldername@myhomefoldername-laptop:~/Coccinella-0.96.12Linux-x86$ chmod +x Coccinella-0.96.12.bin
myhomefoldername@myhomefoldername-laptop:~/Coccinella-0.96.12Linux-x86$ ./Coccinella-0.96.12.bin
./Coccinella-0.96.12.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
myhomefoldername@myhomefoldername-laptop:~/Coccinella-0.96.12Linux-x86$ 

And when I try the other method you recommended, this after copy and pasting the "bin" file into my "home folder" this is the kind of lip it gives me:

myhomefoldername@myhomefoldername-laptop:~$ ln -s ~/bin/Coccinella-0.96.12.bin cocc
ln: creating symbolic link `cocc': File exists
myhomefoldername@myhomefoldername-laptop:~$ cocc
bash: cocc: command not found
myhomefoldername@myhomefoldername-laptop:~$ 

BOGUS!

---

### Post by mb_webguy on 2009-03-20
You just need to install the libstdc++5 package.  The fastest way to do it is by typing "sudo apt-get install libstdc++5" in the terminal, though you could also install it with Synaptic.

Then go back to step #4.  Use the cd command to change to the directory where the .bin file is located, and use the command "./Coccinella-0.96.12.bin" to run it.

Also to create the link, try "ln -s ~/bin/Coccinella-0.96.12.bin cocc", assuming you've moved the .bin file to the ~/bin folder.

---

### Post by Simpotico on 2009-03-21
Okay, here is where I'm at... I installed the "libstdc++5 package" as you recommended and upon repeating step #4 I am able to start Coccinella in the terminal but cannot keep it open once the terminal is closed or find a desktop icon or short cut for the program after it is closed. Remember, I am a rock. I need this spoon fed to me. 

If I am supposed to put the coccinella bin program into the file systems bin folder by some other means then copy and pasting it into there, then I need to be told how; because it isn't letting me do it as it is.

I really need this in a "step by step" formate and in plain English, not ubuntuese. Please, don't assume that I know what you're talking about because I probably don't. I use this thing as a tool. I don't necessarily understand how or why it works, it just does. I just turn it on and wow, it starts faster and works more stable then Windows.

Please, give it to me like you would a five-year-old. Use small words Like, "take the red lego and put it on top of the blue lego, good. Now take the yellow lego and put it on top of the red lego, good. Now take the green lego and put it on top of the yellow lego, good, And so on...

Again, I appreciated your patience with me. I really do want to learn how to do this on my own. But in the; crawl, walk, run phases of learning and competency, I am still very much in the crawl phase when it comes to this.

---

### Post by mb_webguy on 2009-03-21
Ok, I'm assuming you put the Coccinella-0.96.12.bin file in a directory called "bin" in your user's home folder.

Right-click on the Applications/Places/System menu bar, and select Edit Menus.  In the left pane ("Menus:") select "Internet".  Now click the "New Item" button.  This will open a "Create Launcher" window.

In the "Name" box, put something meaningful like "IM Client (Coccinella)".  Click the "Browse" button next to the "Command" box, and locate the Coccinella-0.96.12.bin file.  Now you can select an icon if you want by clicking the icon button in the upper-left corner of the "Create Launcher" window, but it's not necessary.  When you get done, click the "OK" button.

You've just made a launcher -- what Windows would call a shortcut -- to run Coccinella, which you can find in Applications->Internet.  

If you want a launcher on one of the Gnome panels -- the "taskbars" at the top and bottom of the desktop -- right-click on the panel and select "Add to panel".  If you double-click "Custom application launcher" (or single-click and then click the "Add" button), you will be given a "Create Launcher" window.  Fill it out as described above, and you will have a launcher on the panel like the "Quick Launch" icons in Windows.

If you want a launcher on the desktop, right-click on the desktop and select "Create Launcher".  This will again give you a "Create Launcher" window.  Fill it out as described above, and you will have a launcher on the desktop similar to the program shortcuts on the Windows desktop.

If you want Coccinella to start every time you log in, go to System->Preferences->Sessions.  Click the "Add" button.  This will open an "Add Startup Program" window that is identical to the "Create Launcher" window except that it doesn't give you the option to select an icon.  Fill it out as described for the "Create Launcher" window above.  Coccinella will now be added to list of Startup Programs in the "Sessions Preferences" window, and will start automatically every time you log in.

---

