---
title: "cannot run a .bat file"
date: 2009-04-15
forum: General Help
---

### Post by matt12345 on 2009-04-15
Ok I'm trying this new thing out called "Ubuntu", so far it's pretty kool. Bad thing is i cant play on my friends runescape private server witch is a pretty good 1 in my opinion. But yea, anyone know a way to be able to run a .batch file?

Btw,

When i try to run it says 

Run (doesn't work)
Run in terminal (doesn't work)
Display (all it does is show what the code looks like)
and cancel


add my msn if u can help : [email]teh_muffinz0r@hotmail.com[/email]

Oh and I use to be able to run this without any problems when I was using windows. If you need the code I will be very happy to give it to you.

---

### Post by Volt9000 on 2009-04-15
.bat files are command-line scripts used for DOS and Windows environments. They won't work in Linux because they execute programs/commands that don't exist in a Linux environment.

If you post the .bat file here someone can probably convert it to a usable Linux shell script for you, assuming there's no Windows-specific stuff in there. But generally the Linux shell is incredibly powerful, moreso than Windows'.

---

### Post by codeseer on 2009-04-15
Yeah, just post it and we'll probably be able to convert it for you; you may want to replace the server name or IP address in it with something else, like 127.0.0.1, before posting it if privacy is an issue or it could have a password in it you would want to replace. You can open it with gedit (Applications->Accessories->Text Editor), or any other text editor, and look at what it does. It probably just calls the binary and passes your friend's server as a parameter.

---

### Post by 3Miro on 2009-04-15
If it calls for a windows game to run, then you might want consider wine ([www.winehq.com](www.winehq.com))

BTW Linux is a lot different from windows and is in no way new.

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by codeseer on 2009-04-15
> **3Miro said:**
> If it calls for a windows game to run, then you might want consider wine ([www.winehq.com](www.winehq.com))

BTW Linux is a lot different from windows and is in no way new.

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

It's new to them :P

That's a good article to read. I like [these]("http://www.gnu.org/philosophy/philosophy.html") as well; I read them before the switch.

---

### Post by f8l_0e on 2009-04-15
matt12345,

  If the game you are talking about is the game from runescape.com,
then you shouldn't need wine.  Runescape is written in java.  Start a terminal from Applications->Accessories->Terminal and use the following command:

sudo apt-get install java-common

This will get the java runtime library and should also the the plugin for firefox.

We will still need to see the code in your batch script to see how to get it running on linux.

---

### Post by matt12345 on 2009-04-15
thanks so far guys!!

I will definetly post the stuff i need like the information n crap. But i need to know a few things.

1. you need certeen files for it to work, would i need to include those to? If so I will upload the files so people can download them, ect.

2. Also would you just need the code? If so could you convert here. 


3. If you don't mind how could I add them to the folder so i can get it to run?



EDIT:

its not runescape, i dont need java, and i have already tried wine doesnt work =\

---

### Post by codeseer on 2009-04-15
Probably just need the .bat file converted.

---

### Post by matt12345 on 2009-04-15
wat do you mean by that if you dont mind me asking.

---

### Post by Volt9000 on 2009-04-15
> **matt12345 said:**
> thanks so far guys!!

I will definetly post the stuff i need like the information n crap. But i need to know a few things.

1. you need certeen files for it to work, would i need to include those to? If so I will upload the files so people can download them, ect.

2. Also would you just need the code? If so could you convert here. 


3. If you don't mind how could I add them to the folder so i can get it to run?



EDIT:

its not runescape, i dont need java, and i have already tried wine doesnt work =\

1) No you don't need to include the files. However you will need to tell us what this is; i.e. is it a native Windows game? 
Whatever it is, if you can't get it to run even under WINE, then unfortunately you're out of luck. All a .bat file does is facilitate execution of a program by passing parameters to it. If the program itself doesn't run, then converting the batch file to a shell script won't do you much good.

2) All we need is the contents of the .bat file.

3) I'm not sure I understand the question. Add what to what folder? Before you can do anything you need to tell us what it is you're running and paste the code.

---

### Post by codeseer on 2009-04-15
> **matt12345 said:**
> wat do you mean by that if you dont mind me asking.

The .bat file you previously mentioned that you double-click to connect to your friend's server. You can open that up in a text editor and copy/past it here between CODE tags.

---

### Post by matt12345 on 2009-04-15
> **Volt9000 said:**
> 1) No you don't need to include the files. However you will need to tell us what this is; i.e. is it a native Windows game? 
Whatever it is, if you can't get it to run even under WINE, then unfortunately you're out of luck. All a .bat file does is facilitate execution of a program by passing parameters to it. If the program itself doesn't run, then converting the batch file to a shell script won't do you much good. well, I'll try running it  with wine when it's converted.

Yea i guess i would have to say it is a native windows game since all i know of it  working is on windows.
2) All we need is the contents of the .bat file.
here you go


@echo off

COLOR 07

title Deathscape Client

java -Xmx500m -cp .;Theme.jar Gui

pause





3) I'm not sure I understand the question. Add what to what folder? Before you can do anything you need to tell us what it is you're running and paste the code.

Now that you have answered my 3rd question i won't need help with it now. Thanks anyways ;)

---

### Post by matt12345 on 2009-04-15
```
@echo off

COLOR 07

title Deathscape Client

java -Xmx500m -cp .;Theme.jar Gui

pause
```

here it is =o

---

### Post by tom66 on 2009-04-15
The batch program you posted can probably converted to a two-liner script:

```

#!/bin/sh
java -Xmx500m -cp .;Theme.jar Gui

```

Put this in a file called "launch-program.sh" and open a terminal (Applications > Accessories > Terminal under Ubuntu). Type "chmod +x launch-program.sh" (without quotes) to give it executable permissions (this'll let you run it without messing around with other programs, it'll work without this but you'll have to jump through hoops to get it to launch. Put the file in the game's own folder.

Then, to run your new shell script, in a terminal type:

```

cd GAME-FOLDER
./launch-program.sh

```

or double click it in the folder. If it doesn't work let us know what it says back.

---

### Post by codeseer on 2009-04-15
What does that give you when you run it in the terminal from the directory that the .bat file is in? Use the .sh method posted.

If that doesn't work, try changing it to this:

```

java -Xmx500m -cp . -jar Theme.jar Gui

```

---

### Post by matt12345 on 2009-04-15
ill be trying that now tom thanks :D

and when i run it in terminal nothing shows up.

---

### Post by matt12345 on 2009-04-15
if you wouldnt mind explaing how i wuld do:


Put this in a file called "launch-program.sh" and open a terminal (Applications > Accessories > Terminal under Ubuntu). Type "chmod +x launch-program.sh

Then, to run your new shell script, in a terminal type:

Code:

cd GAME-FOLDER
./launch-program.sh

---

### Post by Volt9000 on 2009-04-15
> **matt12345 said:**
> if you wouldnt mind explaing how i wuld do:


Put this in a file called "launch-program.sh" and open a terminal (Applications > Accessories > Terminal under Ubuntu). Type "chmod +x launch-program.sh

Then, to run your new shell script, in a terminal type:

Code:

cd GAME-FOLDER
./launch-program.sh

First run a text editor, by going to Applications > Acessories > Text Editor and copy and paste the code provided, and save the file as "launch-program.sh".

Then bring up a terminal window and type in the commands above. Click Applications > Accessories > Terminal to bring up a terminal window and type in the commands you see. Of course you must substitute "GAME-FOLDER" with the actual folder you saved the .sh file to.

---

### Post by codeseer on 2009-04-15
> **matt12345 said:**
> if you wouldnt mind explaing how i wuld do:


Put this in a file called "launch-program.sh" and open a terminal (Applications > Accessories > Terminal under Ubuntu). Type "chmod +x launch-program.sh

Then, to run your new shell script, in a terminal type:

Code:

cd GAME-FOLDER
./launch-program.sh

Basically, open the folder that has the .bat in it. Right-click in the white space and choose Create Document->Empty File. Type a name in for the file, doesn't matter what you call it, just make sure it ends in .sh. Right-click the file, choose properties, go to the permissions tab, check the box at the bottom that says 'allow executing', click Close. Right-click on the file and choose 'Open with other application', click 'text editor', click 'open'. Now paste the two lines, exactly as they are, that he had in his CODE blocks into the file, click Save.

You'll want to then try double-clicking the file. If it doesn't work for some reason, you'll need to start using the terminal.

---

### Post by tom66 on 2009-04-15
I don't know if you're using GNOME or KDE. Can you tell me (if you have two panels, one on top and one below, you're using GNOME. If you've got a K-themed button, you're using KDE. I think. Long time since I've seen a KDE desktop...)

Assuming you're using GNOME, because that's all I use at the moment:

Click Applications, go to Accessories, open a Text Editor. In the text editor paste what I gave you (the two-liner script). Make sure you've copied the game you're using from Windows to Ubuntu's home folder. Save the script in the folder where the game files are. Use the name "launch-program.sh". 

It would probably be easier to give it executable permissions from Nautilus, the file manager. Open your home folder, navigate to where the game is, and right click on your new file. Select Properties. Under Permissions, check "Allow executing file as a program". Click OK. Double-click on file, and it should work. If it doesn't let us know, and we'll try to figure it out.

---

### Post by matt12345 on 2009-04-15
alright just making the file didnt work but i will try to do in terminal. Also if you don't mind me asking, there were 2 things that you need to do in terminal. Would i need to do both of those in 1 window? or 2? If so 1 then how would i be able to make another paragraph or would i be able to put it together?

---

### Post by codeseer on 2009-04-15
> **matt12345 said:**
> alright just making the file didnt work but i will try to do in terminal. Also if you don't mind me asking, there were 2 things that you need to do in terminal. Would i need to do both of those in 1 window? or 2? If so 1 then how would i be able to make another paragraph or would i be able to put it together?

You won't be typing in the line that started with # in the terminal. However, you can chain commands together by using a semicolon.

---

### Post by matt12345 on 2009-04-15
> **tom66 said:**
> The batch program you posted can probably converted to a two-liner script:

```

#!/bin/sh
java -Xmx500m -cp .;Theme.jar Gui

```

Put this in a file called "launch-program.sh" and open a terminal (Applications > Accessories > Terminal under Ubuntu). Type "chmod +x launch-program.sh" (without quotes) to give it executable permissions (this'll let you run it without messing around with other programs, it'll work without this but you'll have to jump through hoops to get it to launch. Put the file in the game's own folder.

Then, to run your new shell script, in a terminal type:

```

cd GAME-FOLDER
./launch-program.sh

```

or double click it in the folder. If it doesn't work let us know what it says back.

when i tried to do:
launch-program.sh

in terminal it ended up coming up with this

matthew@matthew-desktop:~$ chmod +x launch-program.sh
chmod: cannot access `launch-program.sh': No such file or directory

also the same thing with 


```

cd GAME-FOLDER
./launch-program.sh

```


I'm really sorry to ask this but, is there anyway possible someone could do it for me and if they get it to work give it to me so i can put it in the folder? If you need the whole server file i will upload it and give you the link.

---

### Post by codeseer on 2009-04-15
You can't run it, if you haven't created it yet. Did you create the file (whatever.sh) yet? Are you at the proper path in the terminal?

---

### Post by matt12345 on 2009-04-15
> **codeseer said:**
> You can't run it, if you haven't created it yet. Did you create the file (whatever.sh) yet? Are you at the proper path in the terminal?

yes i created it the file, also yes i made the file, put into the game folder (DeathscapeV4) went into terminal and typed exactly what it said. And got what i posted before

---

### Post by codeseer on 2009-04-15
> **matt12345 said:**
> yes i created it the file, also yes i made the file, put into the game folder (DeathscapeV4) went into terminal and typed exactly what it said. And got what i posted before

You used the text editor and put the content in the file and saved it, right?

Did you change to the DeathscapeV4 directory in the terminal (using the 'cd' command)?

Also, you have to put that ./ in front of the file name when trying to execute it.

---

### Post by matt12345 on 2009-04-15
> **codeseer said:**
> You used the text editor and put the content in the file and saved it, right?

Did you change to the DeathscapeV4 directory in the terminal (using the 'cd' command)?

Also, you have to put that ./ in front of the file name when trying to execute it.

You used the text editor and put the content in the file and saved it, right?    if you mean the deathscape file yes i did 

Did you change to the DeathscapeV4 directory in the terminal (using the 'cd' command)? i tried but got the same thing i got that i posted before.

Also, you have to put that ./ in front of the file name when trying to execute it
By this what do you mean?


And guys I would just really love to say thank for helping me. =]

---

### Post by codeseer on 2009-04-15
I assume you have the Deathscape file on your desktop?

If that is the case, do this in the terminal:

```

cd ~/Desktop/DeathscapeV4
./launch-program.sh

```

Make sure you have the casing correct ('H' is not the same as 'h' on Linux).

---

### Post by Volt9000 on 2009-04-15
Ok try this.
In terminal make sure you're in the proper directory and type

```

ls -l

```

That's a lower-case letter L followed by a lower-case S, a space, a dash then another lower-case L. Then copy and paste the results here. Please make sure to copy the prompt and the command you type, so everything from when you typed the command and onwards.

---

### Post by matt12345 on 2009-04-15
> **codeseer said:**
> I assume you have the Deathscape file on your desktop?

If that is the case, do this in the terminal:

```

cd ~/Desktop/DeathscapeV4
./launch-program.sh

```

Make sure you have the casing correct ('H' is not the same as 'h' on Linux).

yes it is at my desktop but how would i get the ./ when there is another line? Do i hit space? Because if i hit enter it will install it.

---

### Post by codeseer on 2009-04-15
> **matt12345 said:**
> yes it is at my desktop but how would i get the ./ when there is another line? Do i hit space? Because if i hit enter it will install it.

You hit enter after the 'cd' line.

---

### Post by matt12345 on 2009-04-15
> **Volt9000 said:**
> Ok try this.
In terminal make sure you're in the proper directory and type

```

ls -l

```

That's a lower-case letter L followed by a lower-case S, a space, a dash then another lower-case L. Then copy and paste the results here. Please make sure to copy the prompt and the command you type, so everything from when you typed the command and onwards.

here you go.

```
matthew@matthew-desktop:~$ ls -l
total 28
drwxr-xr-x 5 matthew matthew 4096 2009-04-15 21:28 Desktop
drwxr-xr-x 2 matthew matthew 4096 2009-04-15 21:22 Documents
lrwxrwxrwx 1 matthew matthew   26 2009-04-13 16:20 Examples -> /usr/share/example-content
drwxr-xr-x 2 matthew matthew 4096 2009-04-13 16:28 Music
drwxr-xr-x 2 matthew matthew 4096 2009-04-13 16:28 Pictures
drwxr-xr-x 2 matthew matthew 4096 2009-04-13 16:28 Public
drwxr-xr-x 2 matthew matthew 4096 2009-04-13 16:28 Templates
drwxr-xr-x 2 matthew matthew 4096 2009-04-13 16:28 Videos
matthew@matthew-desktop:~$ 


```

---

### Post by Volt9000 on 2009-04-15
Ok so you're not in the correct directory where you saved the file.
I'll assume you created the directory on your Desktop, so now type this:

```

cd Desktop/DeathscapeV4

```

This will change to the appropriate directory. I'm assuming you have a directory called "DeathscapeV4" on your desktop.
Now re-run that "ls -l" command from my last post.

---

### Post by codeseer on 2009-04-15
Now type:

```

cd ~/Desktop

```

Hit enter.

Then type:

```

ls -l

```

And post that.

---

### Post by matt12345 on 2009-04-15
> **Volt9000 said:**
> Ok so you're not in the correct directory where you saved the file.
I'll assume you created the directory on your Desktop, so now type this:

```

cd Desktop/DeathscapeV4

```

This will change to the appropriate directory. I'm assuming you have a directory called "DeathscapeV4" on your desktop.
Now re-run that "ls -l" command from my last post.

for you (seer i will do urs in a sec)

-rwx------ 1 matthew matthew  10116 2009-02-14 23:43 Applet_Sub1.class
-rwx------ 1 matthew matthew   2108 2009-02-14 23:43 Bluurr.class
drwx------ 2 matthew matthew   4096 2009-04-14 17:31 cache
-rwx------ 1 matthew matthew    421 2009-02-14 23:43 Class10.class
-rwx------ 1 matthew matthew   7366 2009-02-14 23:43 Class11.class
-rwx------ 1 matthew matthew   2055 2009-02-14 23:43 Class12.class
-rwx------ 1 matthew matthew   7853 2009-02-14 23:43 Class13.class
-rwx------ 1 matthew matthew   4028 2009-02-14 23:43 Class14.class
-rwx------ 1 matthew matthew   2720 2009-02-14 23:43 Class15.class
-rwx------ 1 matthew matthew   3258 2009-02-14 23:43 Class16.class
-rwx------ 1 matthew matthew   2603 2009-02-14 23:43 Class17.class
-rwx------ 1 matthew matthew    682 2009-02-14 23:43 Class18.class
-rwx------ 1 matthew matthew   1786 2009-02-14 23:43 Class19.class
-rwx------ 1 matthew matthew   1565 2009-02-14 23:43 Class1.class
-rwx------ 1 matthew matthew   2934 2009-02-14 23:43 Class20.class
-rwx------ 1 matthew matthew    529 2009-02-14 23:43 Class21.class
-rwx------ 1 matthew matthew   3274 2009-02-14 23:43 Class22.class
-rwx------ 1 matthew matthew   3368 2009-02-14 23:43 Class23.class
-rwx------ 1 matthew matthew   3901 2009-02-14 23:43 Class24.class
-rwx------ 1 matthew matthew  39646 2009-02-14 23:43 Class25.class
-rwx------ 1 matthew matthew    388 2009-02-14 23:43 Class26.class
-rwx------ 1 matthew matthew    648 2009-02-14 23:43 Class27.class
-rwx------ 1 matthew matthew    502 2009-02-14 23:43 Class28.class
-rwx------ 1 matthew matthew   1770 2009-02-14 23:43 Class29.class
-rwx------ 1 matthew matthew   1293 2009-02-14 23:43 Class2.class
-rwx------ 1 matthew matthew    500 2009-02-14 23:43 Class30.class
-rwx------ 1 matthew matthew    456 2009-02-14 23:43 Class30_Sub1.class
-rwx------ 1 matthew matthew    452 2009-02-14 23:43 Class30_Sub2.class
-rwx------ 1 matthew matthew   3888 2009-02-14 23:43 Class30_Sub2_Sub1.class
-rwx------ 1 matthew matthew  30956 2009-02-14 23:43 Class30_Sub2_Sub1_Sub1.class
-rwx------ 1 matthew matthew   4730 2009-02-14 23:43 Class30_Sub2_Sub1_Sub2.class
-rwx------ 1 matthew matthew  25500 2009-02-14 23:43 Class30_Sub2_Sub1_Sub3.class
-rwx------ 1 matthew matthew   8320 2009-02-14 23:43 Class30_Sub2_Sub1_Sub4.class
-rwx------ 1 matthew matthew  10599 2009-02-14 23:43 Class30_Sub2_Sub2.class
-rwx------ 1 matthew matthew    348 2009-02-14 23:43 Class30_Sub2_Sub3.class
-rwx------ 1 matthew matthew    681 2009-02-14 23:43 Class30_Sub2_Sub4.class
-rwx------ 1 matthew matthew   3492 2009-02-14 23:43 Class30_Sub2_Sub4_Sub1.class
-rwx------ 1 matthew matthew   2458 2009-02-14 23:43 Class30_Sub2_Sub4_Sub1_Sub1.class
-rwx------ 1 matthew matthew   8133 2009-02-14 23:43 Class30_Sub2_Sub4_Sub1_Sub2.class
-rwx------ 1 matthew matthew    555 2009-02-14 23:43 Class30_Sub2_Sub4_Sub2.class
-rwx------ 1 matthew matthew   2250 2009-02-14 23:43 Class30_Sub2_Sub4_Sub3.class
-rwx------ 1 matthew matthew   3338 2009-02-14 23:43 Class30_Sub2_Sub4_Sub4.class
-rwx------ 1 matthew matthew   2440 2009-02-14 23:43 Class30_Sub2_Sub4_Sub5.class
-rwx------ 1 matthew matthew  30300 2009-02-14 23:43 Class30_Sub2_Sub4_Sub6.class
-rwx------ 1 matthew matthew    999 2009-02-14 23:43 Class30_Sub3.class
-rwx------ 1 matthew matthew   3549 2009-02-14 23:43 Class31.class
-rwx------ 1 matthew matthew   1940 2009-02-14 23:43 Class32.class
-rwx------ 1 matthew matthew    272 2009-02-14 23:43 Class33.class
-rwx------ 1 matthew matthew  14696 2009-02-14 23:43 Class34.class
-rwx------ 1 matthew matthew   2400 2009-02-14 23:43 Class35.class
-rwx------ 1 matthew matthew   2630 2009-02-14 23:43 Class36.class
-rwx------ 1 matthew matthew   1926 2009-02-14 23:43 Class37.class
-rwx------ 1 matthew matthew   2997 2009-02-14 23:43 Class38.class
-rwx------ 1 matthew matthew   2791 2009-02-14 23:43 Class39.class
-rwx------ 1 matthew matthew    402 2009-02-14 23:43 Class3.class
-rwx------ 1 matthew matthew   5113 2009-02-14 23:43 Class40.class
-rwx------ 1 matthew matthew   2352 2009-02-14 23:43 Class41.class
-rwx------ 1 matthew matthew    295 2009-02-14 23:43 Class42.class
-rwx------ 1 matthew matthew  13148 2009-02-14 23:43 Class42_Sub1.class
-rwx------ 1 matthew matthew    495 2009-02-14 23:43 Class43.class
-rwx------ 1 matthew matthew   1770 2009-02-14 23:43 Class44.class
-rwx------ 1 matthew matthew    982 2009-02-14 23:43 Class45.class
-rwx------ 1 matthew matthew  11581 2009-02-14 23:43 Class46.class
-rwx------ 1 matthew matthew    538 2009-02-14 23:43 Class47.class
-rwx------ 1 matthew matthew   1030 2009-02-14 23:43 Class48.class
-rwx------ 1 matthew matthew    350 2009-02-14 23:43 Class49.class
-rwx------ 1 matthew matthew    966 2009-02-14 23:43 Class4.class
-rwx------ 1 matthew matthew   2935 2009-02-14 23:43 Class50.class
-rwx------ 1 matthew matthew  15211 2009-02-14 23:43 Class5.class
-rwx------ 1 matthew matthew   5468 2009-02-14 23:43 Class6.class
-rwx------ 1 matthew matthew  16509 2008-09-13 12:37 Class7.class
-rwx------ 1 matthew matthew  78773 2009-02-14 23:43 Class8.class
-rwx------ 1 matthew matthew  57747 2009-02-14 23:43 Class9.class
-rwx------ 1 matthew matthew 215508 2009-02-14 23:43 client.class
-rwx------ 1 matthew matthew     90 2008-12-26 00:21 compile.bat
drwx------ 5 matthew matthew   4096 2009-04-14 17:31 contrib
-rwx------ 1 matthew matthew     34 2008-11-11 17:52 demo.bat
-rwx------ 1 matthew matthew   1234 2008-08-12 09:11 FileOperations.class
drwx------ 7 matthew matthew   4096 2009-04-14 17:31 Files
-rwx------ 1 matthew matthew    898 2009-02-14 23:43 Frame_Sub1.class
-rwx------ 1 matthew matthew   2124 2009-02-14 23:43 Gui$1.class
-rwx------ 1 matthew matthew  18512 2009-02-14 23:43 Gui.class
-rwx------ 1 matthew matthew    792 2009-02-14 23:43 Gui$imageFileFilter.class
-rwxrwxrwx 1 matthew matthew     39 2009-04-15 22:28 launch-program.sh
-rw-rw-rw- 1 matthew matthew     44 2009-04-15 21:44 launch-program.sh~
drwx------ 3 matthew matthew   4096 2009-04-14 17:31 Models
-rwx------ 1 matthew matthew   1133 2009-01-28 20:03 MP3Player.class
drwx------ 3 matthew matthew   4096 2009-04-14 17:31 org
-rwx------ 1 matthew matthew   2101 2009-02-14 23:43 ProgressChecker.class
drwx------ 3 matthew matthew   4096 2009-04-14 17:31 resource
-rwx------ 1 matthew matthew     86 2009-01-31 16:08 run.bat
-rwx------ 1 matthew matthew    790 2008-03-01 16:20 SAXParser.class
drwx------ 2 matthew matthew   4096 2009-04-14 17:31 sign
-rwx------ 1 matthew matthew   3414 2009-02-14 23:43 Update.class
-rwx------ 1 matthew matthew   1096 2009-02-14 23:43 Updater.class
drwx------ 4 matthew matthew   4096 2009-04-14 17:31 User
-rwx------ 1 matthew matthew   3280 2009-02-14 23:43 UserLoader.class
-rwx------ 1 matthew matthew    944 2008-03-01 16:20 VersionGetter.class
-rwx------ 1 matthew matthew     40 2008-11-02 18:05 Version.xml
-rwx------ 1 matthew matthew   5140 2009-02-14 23:43 Xml$.class
matthew@matthew-desktop:~/Desktop/DeathscapeV4$

---

### Post by Volt9000 on 2009-04-15
```

-rwxrwxrwx 1 matthew matthew 39 2009-04-15 22:28 launch-program.sh

```

Ok there it is, that's the program you saved.
See all those x's in the first column? That means this program is set to executable.
So now to run it, from this directory that you're in, just type

```

./launch-program.sh

```

Make sure to type the dot-slash at the beginning.

---

### Post by codeseer on 2009-04-15
You don't need to do mine now. That's the right directory.

Now type:

```

./launch-program.sh

```

---

### Post by matt12345 on 2009-04-15
```
matthew@matthew-desktop:~$ cd  ~/Desktop
matthew@matthew-desktop:~/Desktop$ ls -l
total 45316
-rwxrwxrwx  1 matthew matthew  2616897 2009-04-14 14:57 amsn-0.97.2-1.tcl85.x86.package
drwx------ 10 matthew matthew     4096 2009-04-15 22:28 DeathscapeV4
drwxr-xr-x  2 matthew matthew     4096 2009-04-15 21:24 GAME-Deathscapev4
-rwxrwxrwx  1 matthew matthew 19635520 2009-04-15 12:13 jre-6u13-linux-i586-rpm.bin
-rw-r--r--  1 matthew matthew     8004 2009-04-15 21:09 launch-program.sh
drwxr-xr-x  2 matthew matthew     4096 2009-04-15 21:12 LimeWireLinux
-rw-r--r--  1 matthew matthew 24068410 2009-04-15 19:24 LimeWireLinux.deb
-rw-r--r--  1 matthew matthew        0 2009-04-15 21:28 new file
matthew@matthew-desktop:~/Desktop$ 

```

---

### Post by matt12345 on 2009-04-15
> **codeseer said:**
> You don't need to do mine now. That's the right directory.

Now type:

```

./launch-program.sh

```

i think im doing something wrong but idk :\



```
matthew@matthew-desktop:~$ ./launch-program.sh
bash: ./launch-program.sh: No such file or directory
matthew@matthew-desktop:~$ 

```

---

### Post by codeseer on 2009-04-15
You need to type:

```

cd DeathscapeV4

```

Before typing:

```

./launch-program.sh

```

---

### Post by matt12345 on 2009-04-15
plz tell me im doing something wrong =\


matthew@matthew-desktop:~$ cd  DeathscapeV4                                      ./launch-program.sh
bash: cd: DeathscapeV4: No such file or directory
matthew@matthew-desktop:~$ cd  DeathscapeV4
bash: cd: DeathscapeV4: No such file or directory
matthew@matthew-desktop:~$ ./launch-program.sh
bash: ./launch-program.sh: No such file or directory
matthew@matthew-desktop:~$ cd DeathscapeV4
bash: cd: DeathscapeV4: No such file or directory
matthew@matthew-desktop:~$ cd DeathscapeV4 ./launch-program.sh
bash: cd: DeathscapeV4: No such file or directory
matthew@matthew-desktop:~$

---

### Post by Volt9000 on 2009-04-15
Ok, hold up a sec. You don't seem to understand what you have to do.

First thing you have to do is change to the directory of interest. In this case, the directory is called DeathscapeV4 and it's located on your desktop.

So when you open up a terminal window you are initially in your home directory, as presented by this prompt:

```

matthew@matthew-desktop:~$

```

See the little ~ right before the dollar sign? That's your home directory. Now you need to get to DeathscapeV4 on your desktop. So type:

```

cd Desktop/DeathscapeV4

```

And hit Enter. Now your prompt should look like:

```

matthew@matthew-desktop:~/Desktop/DeathscapeV4$ 

```

Now you're in the right directory.
And NOW you type:

```

./launch-program.sh

```

---

### Post by codeseer on 2009-04-15
Looks like you got back to the home directory some how.

Type this in, exactly, then hit enter:

```

cd ~/Desktop/DeathscapeV4; ./launch-program.sh

```

---

### Post by matt12345 on 2009-04-15
> **Volt9000 said:**
> Ok, hold up a sec. You don't seem to understand what you have to do.

First thing you have to do is change to the directory of interest. In this case, the directory is called DeathscapeV4 and it's located on your desktop.

So when you open up a terminal window you are initially in your home directory, as presented by this prompt:

```

matthew@matthew-desktop:~$

```

See the little ~ right before the dollar sign? That's your home directory. Now you need to get to DeathscapeV4 on your desktop. So type:

```

cd Desktop/DeathscapeV4

```

And hit Enter. Now your prompt should look like:

```

matthew@matthew-desktop:~/Desktop/DeathscapeV4$ 

```

Now you're in the right directory.
And NOW you type:

```

./launch-program.sh

```

did exactly what u said to do and got:

```
matthew@matthew-desktop:~$ cd  Desktop/DeathscapeV4
matthew@matthew-desktop:~/Desktop/DeathscapeV4$ ./launch-program.sh
./launch-program.sh: line 1: java: command not found
matthew@matthew-desktop:~/Desktop/DeathscapeV4$ 

```

do i need java or anything like that?

---

### Post by matt12345 on 2009-04-15
> **codeseer said:**
> Looks like you got back to the home directory some how.

Type this in, exactly, then hit enter:

```

cd ~/Desktop/DeathscapeV4; ./launch-program.sh

```

same thing for you codeseer :\

```
matthew@matthew-desktop:~$ cd ~/Desktop/DeathscapeV4;  ./launch-program.sh
./launch-program.sh: line 1: java: command not found
matthew@matthew-desktop:~/Desktop/DeathscapeV4$ 

```

---

### Post by Volt9000 on 2009-04-15
Of course you need Java! ;)

Type the following:

```

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

```

After you type this and hit Enter you'll be asked for your password. This is your account's password, the same you use when you log in. Once you type it in and hit Enter, let apt-get work its magic and Java will be installed. Then run your program again:

```

./launch-program.sh

```

---

### Post by codeseer on 2009-04-15
> **Volt9000 said:**
> Of course you need Java! ;)

Type the following:

```

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

```

After you type this and hit Enter you'll be asked for your password. This is your account's password, the same you use when you log in. Once you type it in and hit Enter, let apt-get work its magic and Java will be installed. Then run your program again:

```

./launch-program.sh

```

```
$ face --keyboard
```

I guess it worked, since he hasn't posted again.

---

### Post by matt12345 on 2009-04-16
umm ill try it, sorry i just had to go to bed :x

---

### Post by matt12345 on 2009-04-16
ummm? :\

```
matthew@matthew-desktop:~$ sudo  apt-get install sun-java6-jre sun java6-plugin sun-java6-fonts
[sudo] password for matthew: 
Sorry, try again.
[sudo] password for matthew: 
Sorry, try again.
[sudo] password for matthew: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

---

### Post by codeseer on 2009-04-16
You'll need to enter your password when it asks there. It is the same password you entered when it asked for one at the time you installed Ubuntu. It is case sensitive, meaning that capital and lower case letters must be entered exactly as you did when you installed Ubuntu. It will not show any asterisks (*) while you are entering the password; it won't show any placeholders, but if you just enter it and then press Enter, it will take it if you entered the correct password.

---

### Post by matt12345 on 2009-04-16
it told me i needed to install something so i installed it and i got:

```
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-10-0ubuntu2) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-10-0ubuntu2) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
  sun-java6-plugin: Depends: sun-java6-bin (= 6-10-0ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
matthew@matthew-desktop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```

---

### Post by codeseer on 2009-04-16
> **matt12345 said:**
> it told me i needed to install something so i installed it and i got:

```
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-10-0ubuntu2) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-10-0ubuntu2) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
  sun-java6-plugin: Depends: sun-java6-bin (= 6-10-0ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
matthew@matthew-desktop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```

Type:

```

sudo apt-get -f install

```

Anytime it says that you don't have permissions, you can gain them by typing sudo before the command.

---

### Post by matt12345 on 2009-04-16
ok i did wat u said and got this:

```
matthew@matthew-desktop:~$ sudo apt-get -f install
[sudo] password for matthew: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gsfonts-x11 odbcinst1debian1 sun-java6-bin sun-java6-jre unixodbc xutils-dev
Suggested packages:
  sun-java6-plugin ia32-sun-java6-plugin sun-java6-fonts libmyodbc
  odbc-postgresql libct1
The following NEW packages will be installed:
  gsfonts-x11 odbcinst1debian1 sun-java6-bin unixodbc xutils-dev
The following packages will be upgraded:
  sun-java6-jre
1 upgraded, 5 newly installed, 0 to remove and 282 not upgraded.
1 not fully installed or removed.
Need to get 0B/35.2MB of archives.
After this operation, 102MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

should i hit Y?

---

### Post by codeseer on 2009-04-16
Yep, hit 'Y'. Then you'll probably need to press Enter.

You also have "282 not upgraded"; which can be addressed after we get Java ready and try to run the game again.

---

### Post by matt12345 on 2009-04-16
ok i got java and got everything i need. But i tried to do the code you left on page 5 i believ and i got this :

```
matthew@matthew-desktop:~$ cd ~/Desktop/DeathscapeV4;  ./launch-program.sh
Unable to access jarfile Theme.jar

```

---

### Post by codeseer on 2009-04-16
> **matt12345 said:**
> ok i got java and got everything i need. But i tried to do the code you left on page 5 i believ and i got this :

```
matthew@matthew-desktop:~$ cd ~/Desktop/DeathscapeV4;  ./launch-program.sh
Unable to access jarfile Theme.jar

```

Something is missing from our puzzle. There's no Theme.jar in that download.

If you type:

```

java -Xmx500m Gui

```

That works, does it not?

---

### Post by matt12345 on 2009-04-16
im sorry to ask this but where would i put that?

---

### Post by codeseer on 2009-04-16
> **matt12345 said:**
> im sorry to ask this but where would i put that?

In the terminal:

```

cd ~/Desktop/DeathscapeV4; java -Xmx500m Gui

```

---

### Post by matt12345 on 2009-04-16
it works :D

although when you switch tabs for like food or prayer if you know what im talking about. It shows the tab that you used before and it keeps pileing up till you cant see anything. Any ideas? :\

---

### Post by codeseer on 2009-04-16
> **matt12345 said:**
> it works :D

although when you switch tabs for like food or prayer if you know what im talking about. It shows the tab that you used before and it keeps pileing up till you cant see anything. Any ideas? :\

Sounds like a graphics issue. Try applying those 200 some updates you had and restarting, then see if it works any better. If not, then make sure you have an up-to-date video driver selected from System->Administration->Hardware Drivers.

Edit:

Do you see the Orange star shape in the upper right corner of your screen? That means you have updates, click on that.

---

### Post by matt12345 on 2009-04-16
> **codeseer said:**
> Sounds like a graphics issue. Try applying those 200 some updates you had and restarting, then see if it works any better. If not, then make sure you have an up-to-date video driver selected from System->Administration->Hardware Drivers.

Edit:

Do you see the Orange star shape in the upper right corner of your screen? That means you have updates, click on that.

ill install all the updates and get back to u in a few minutes

EDIT:

ill get back to you in like 2 hours or so :s

hopefully it will work, but if it doesn't i just want to really thank you helping me =]. Is there any way I could thank you? >_>

EDIT again:

since my  system is not the best it'll take like 15 hours to install 287 items :x

---

### Post by codeseer on 2009-04-16
> **matt12345 said:**
> ill install all the updates and get back to u in a few minutes

EDIT:

ill get back to you in like 2 hours or so :s

hopefully it will work, but if it doesn't i just want to really thank you helping me =]. Is there any way I could thank you? >_>

EDIT again:

since my  system is not the best it'll take like 15 hours to install 287 items :x

Alright, I have this thread subscribed; so, I'll see when you post again.

---

### Post by matt12345 on 2009-04-16
Alright I have installed everything and it is acting the same. Any ideas?

---

### Post by tom66 on 2009-04-16
Have you restarted your computer? Sometimes you have to do this for graphics drivers to take effect. Also, can you tell me what the output of the command 'lspci' is?

---

### Post by codeseer on 2009-04-16
Yeah, make sure you restarted after the updates.

Did you go to System->Administration->Hardware Drivers and make sure the top one on the list has a green bubble beside it?

Also, do like tom said and open a terminal and type this in:

```

lspci | grep VGA

```

---

### Post by matt12345 on 2009-04-16
alright i did wat u did and it came up with 

```
matthew@matthew-desktop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)

```

When i went to hardware drivers it said that i had nothing in it.

---

### Post by tom66 on 2009-04-16
Great - Intel are usually fantastic with Linux. It shouldn't have any restricted drivers as Intel's drivers are unrestricted / open source. (Is this a laptop or a desktop?)

After reboot does the problem still occur?

---

### Post by matt12345 on 2009-04-16
Its a  desktop. And why reboot?

---

### Post by codeseer on 2009-04-16
After that many updates and considering the type of updates, it is very wise to reboot. It should have prompted you really.

---

### Post by matt12345 on 2009-04-16
rebooted twice nothing =\

Could it possibly be i'm missing something in the games folder?

---

### Post by tom66 on 2009-04-17
Make sure you've copied everything over, then try running again. Do you see any messages written in the terminal when you run the program?

---

### Post by matt12345 on 2009-04-17
nothing out of the usual exept i just got this:

```
matthew@matthew-desktop:~$ cd Desktop/DeathscapeV4
matthew@matthew-desktop:~/Desktop/DeathscapeV4$ ./launch-program.sh
Unable to access jarfile Theme.jar
matthew@matthew-desktop:~/Desktop/DeathscapeV4$ java -Xmx500m Gui

Connecting to update server
no midi or mp3 files in folder
connected to update server
javax.sound.midi.MidiUnavailableException: Audio Device Unavailable
	at com.sun.media.sound.MixerSynth.implOpen(MixerSynth.java:165)
	at com.sun.media.sound.AbstractMidiDevice.doOpen(AbstractMidiDevice.java:144)
	at com.sun.media.sound.AbstractMidiDevice.openInternal(AbstractMidiDevice.java:134)
	at com.sun.media.sound.AbstractMidiDevice.getReceiverReferenceCounting(AbstractMidiDevice.java:339)
	at javax.sound.midi.MidiSystem.getReceiver(MidiSystem.java:243)
	at javax.sound.midi.MidiSystem.getSequencer(MidiSystem.java:442)
	at javax.sound.midi.MidiSystem.getSequencer(MidiSystem.java:348)
	at sign.signlink.run(signlink.java:125)
	at java.lang.Thread.run(Thread.java:619)
loading custom spirts part 1
loading custom spirts part 2

```


and if anyone needs a picture of it i dont mind.

---

### Post by codeseer on 2009-04-17
Yeah, go ahead and give us a picture of the occurrence. Perhaps it will help in the diagnosis.

---

### Post by matt12345 on 2009-04-17
[IMG]http://i39.tinypic.com/2ec3uhe.png[/IMG]

as u can see there are over lapping back grounds.

---

### Post by codeseer on 2009-04-17
Did you have anything else in the folder when you ran it in Windows? I'm just wondering if you needed that Theme.jar file; that maybe Deathscape is supposed to be copied over-top of something else.

---

### Post by matt12345 on 2009-04-17
umm i dont kno, but ill try re-downloading it.

---

### Post by codeseer on 2009-04-17
Maybe try:

```

java -Xmx500m client Gui

```

---

### Post by matt12345 on 2009-04-17
tried ur idea but got this error:


```
matthew@matthew-desktop:~$ cd Desktop/DeathscapeV4
matthew@matthew-desktop:~/Desktop/DeathscapeV4$ ./launch-program.sh
Unable to access jarfile Theme.jar
matthew@matthew-desktop:~/Desktop/DeathscapeV4$ java -Xmx500m client Gui
javax.sound.midi.MidiUnavailableException: Audio Device Unavailable
	at com.sun.media.sound.MixerSynth.implOpen(MixerSynth.java:165)
	at com.sun.media.sound.AbstractMidiDevice.doOpen(AbstractMidiDevice.java:144)
	at com.sun.media.sound.AbstractMidiDevice.openInternal(AbstractMidiDevice.java:134)
	at com.sun.media.sound.AbstractMidiDevice.getReceiverReferenceCounting(AbstractMidiDevice.java:339)
	at javax.sound.midi.MidiSystem.getReceiver(MidiSystem.java:243)
	at javax.sound.midi.MidiSystem.getSequencer(MidiSystem.java:442)
	at javax.sound.midi.MidiSystem.getSequencer(MidiSystem.java:348)
	at sign.signlink.run(signlink.java:125)
	at java.lang.Thread.run(Thread.java:619)

```

also wont let me login :(

ill try redownloading it after dinner so brb ;o

---

### Post by matt12345 on 2009-04-17
redownloaded nothing changed =\

---

### Post by codeseer on 2009-04-17
> **matt12345 said:**
> redownloaded nothing changed =\

There's a message on their site that says they're taking the servers down temporarily. That error is the same one you get with the previous command, so when the servers come back up it should let you log in and give that new command a try.

---

### Post by matt12345 on 2009-04-17
What exactly do you mean as in not on?

I'm on it right know.

---

### Post by codeseer on 2009-04-17
> **matt12345 said:**
> What exactly do you mean as in not on?

I'm on it right know.

Oh, so the old command works but the new one doesn't?

Have you tried asking in the Deathscape forums? The author of it might have a better clue about what's going on. I'd do that and explain to him that you are trying to get it running on Linux and can't use the command in the batch file because there's no Theme.jar. Also, tell them about the overlapping. I'd say that the problem is because you're missing that Theme.jar or because of a graphical glitch that occurs when ran on Linux as compared to Windows. If it's a glitch, then it is probably because the bag/icon area there isn't updated when the tabs are clicked. I don't think you're having that problem on the map area, because it updates the draw frequently. It may be that the author of Deathscape just needs to add a refresh call for that area after a tab is clicked; but he's the one with the source code.

---

### Post by tom66 on 2009-04-18
I would suggest that open source Java runtimes might help, but I don't know what one to suggest. Perhaps codeseer will know.

---

### Post by bendib on 2009-04-19
> **matt12345 said:**
> 
its not runescape, i dont need java, and i have already tried wine doesnt work =\ You can't just install wine and expect it to work. Right click the file, and select properties, under open with, choose wine.
Then click close and it should work.

---

### Post by codeseer on 2009-04-19
> **bendib said:**
> You can't just install wine and expect it to work. Right click the file, and select properties, under open with, choose wine.
Then click close and it should work.

It's written in Java.

---

### Post by Volt9000 on 2009-04-19
It sounds like it's a platform-specific bug. *Might* have something to do with Theme.jar but I don't think so.

Best thing to do is to bring this issue to the attention of the developers.

---

### Post by matt12345 on 2009-04-20
Ok, in the past day i have talken to the owner, co owner, and 3 of the coders. None of them have any idea whats going on =\

---

### Post by Volt9000 on 2009-04-21
> **matt12345 said:**
> Ok, in the past day i have talken to the owner, co owner, and 3 of the coders. None of them have any idea whats going on =\

Hm.... well unfortunately this issue is out of our hands.

I wonder, did they try to reproduce the issue, or did they just say "Sorry, dunno"?

---

### Post by codeseer on 2009-04-21
I still say it's to do with that Theme.jar.

---

### Post by matt12345 on 2009-04-21
I agree with code, i think it would work again if i had the theme.jar but idk how to get :s

---

### Post by codeseer on 2009-04-21
Did you ask the creators what the Theme.jar was about? They're the ones that put it in the batch file, so they should know. My guess is it is a file you need to serve as part of the graphical overlay for the game; thus, it could solve your problem.

---

### Post by Volt9000 on 2009-04-21
Interesting, because I didn't find it in the .rar download.

matt, do you have a previous version of Deathscape, i.e. pre-version 4? Maybe they just forgot to include it in this particular .rar file, but it existed in previous ones. If you do have an older version look in that .rar and see if it's there.

---

### Post by matt12345 on 2009-04-22
I do not have a previous version but I'm sure if i dug around i culd find 1.

---

### Post by Volt9000 on 2009-04-22
You should ask the developers if they tested this on multiple platforms. Since it's written in Java it shouldn't be an issue to begin with, but you never know with these kinds of things.

You could also ask them directly about Theme.jar. They might tell you that yes indeed, it is necessary, and it is what's causing the problem.

Did you mention to them originally about the error message saying that file can't be found? Maybe that's why they can't reproduce it-- if they already have it.

---

