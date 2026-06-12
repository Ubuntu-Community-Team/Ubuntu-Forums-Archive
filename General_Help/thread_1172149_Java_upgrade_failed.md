---
title: "Java upgrade failed"
date: 2009-05-28
forum: General Help
---

### Post by Pinon on 2009-05-28
I am a linux ubuntu user, but not a pro.

I need help with overcoming this obstacle.

I tried to upgrade Java, downloaded the latest update from java.com.

I had to use the Terminal trying to install it.... :s

Then I got these failed dependencies... :p



root@birgit-laptop:/home/johnny# rpm -iv jre-6u13-linux-i586.rpm
feil: Failed dependencies:
	/bin/basename is needed by jre-1.6.0_13-fcs.i586
	/bin/cat is needed by jre-1.6.0_13-fcs.i586
	/bin/cp is needed by jre-1.6.0_13-fcs.i586
	/bin/gawk is needed by jre-1.6.0_13-fcs.i586
	/bin/grep is needed by jre-1.6.0_13-fcs.i586
	/bin/ln is needed by jre-1.6.0_13-fcs.i586
	/bin/ls is needed by jre-1.6.0_13-fcs.i586
	/bin/mkdir is needed by jre-1.6.0_13-fcs.i586
	/bin/mv is needed by jre-1.6.0_13-fcs.i586
	/bin/pwd is needed by jre-1.6.0_13-fcs.i586
	/bin/rm is needed by jre-1.6.0_13-fcs.i586
	/bin/sed is needed by jre-1.6.0_13-fcs.i586
	/bin/sort is needed by jre-1.6.0_13-fcs.i586
	/bin/touch is needed by jre-1.6.0_13-fcs.i586
	/usr/bin/cut is needed by jre-1.6.0_13-fcs.i586
	/usr/bin/dirname is needed by jre-1.6.0_13-fcs.i586
	/usr/bin/expr is needed by jre-1.6.0_13-fcs.i586
	/usr/bin/find is needed by jre-1.6.0_13-fcs.i586
	/usr/bin/tail is needed by jre-1.6.0_13-fcs.i586
	/usr/bin/tr is needed by jre-1.6.0_13-fcs.i586
	/usr/bin/wc is needed by jre-1.6.0_13-fcs.i586
	/bin/sh is needed by jre-1.6.0_13-fcs.i586
root@birgit-laptop:/home/johnny# 


I have no idea how to solve this.


Greetings,
Pinon

---

### Post by Legace on 2009-05-28
Umm.. Why did you download a RMP package for Debian (.deb) based Ubuntu?

And, update manager should update Java automatically. Try it first.

---

### Post by Pinon on 2009-06-20
Lol, wrong package :p
Update manager do not fix the issue.
The old or wrong version of java hinders me from loging in to my bank. 

At [www.java.com](www.java.com) I am told: 

Verifying Java Version
Oops! You don't have the recommended Java installed.
Your Java version is 1.6.0_0. Please click the button below to get the recommended Java for your computer.  
[End of quotation.]

Following the instructions given at java.com for updating my system, has many obstacles for me to overcome, (such as I have no root, and managing commands at the Terminal) and I have a hard time to getting through.

---

### Post by EarthMind on 2009-06-20
What do you mean with you have no root? Can't you use the "sudo" command?

Plus, you should download the .bin file and install that one, e.g. in /opt/java and create symbolic links to the browser plugin in that directory.

---

### Post by Pinon on 2009-06-20
At java.com the instructions start with the following:

" To install the Linux (self-extracting) file     Follow these instructions:

   1. At the terminal: Type:
      su
   2. Enter the root password.
" [Quot. end]


So I do this: (Typing "su)

"
johnny@birgit-laptop:~$ su
Password: 
su: Authentication failure
johnny@birgit-laptop:~$
" [Quot. end]

I guess my ubuntu has no root.

---

### Post by Soul-Sing on 2009-06-20
Ubuntu uses sudo, su is not active on Ubuntu.
Instead of using su, try: sudo -i.

---

### Post by michy99 on 2009-06-20
Ubuntu has the root login disabled by default. You use sudo instead. Whenever a command needs root permissions, just use the word sudo in front of it. For example, if you enter the command```
cp somefile /opt/example
``` and it says you don't have permission, just use```
sudo cp somefile /opt/example
``` instead.

---

### Post by Pinon on 2009-06-20
Ok, I will try the sudo -i.

By the way, how do I create symbolic links to the browser plugin? I use Firefox.

I quote previous post:

"Plus, you should download the .bin file and install that one, e.g. in /opt/java and create symbolic links to the browser plugin in that directory."


Thank you to you too, michy99, that was informative!

---

### Post by EarthMind on 2009-06-20
[SIZE="5"]**[COLOR="RoyalBlue"]Here are the complete instructions to install Java, assuming you've downloaded the .bin version.[/COLOR]**[/SIZE]

**1.** Browse to the directory where you want to install java and create it if it doesn't already exist, e.g. /opt/java
```
sudo mkdir /opt/java
cd /opt/java
```

**2.** Now make sure the file is executable
```
chmod a+x /path/to/file/jre-6u14-linux-i586.bin
```

**3.** Start the installation process
```
sudo /path/to/file/jre-6u14-linux-i586.bin
```

[COLOR="DimGray"]
This displays a binary license agreement. Read through the agreement. Press the spacebar to display the next page. At the end, enter **yes** to proceed with the installation.[/COLOR]

This should've created the /opt/java/jre1.6.0_14 directory.

**4.** Now copy the files to the /opt/java directory
```
sudo cp -R /opt/java/jre1.6.0_14/* /opt/java
```

**5. **Lastly, delete the jre1.6.0_14 subfolder
```
sudo rm -r /opt/java/jre1.6.0_14
```

Now you've successfully installed Java on your system but we're far from done.

**6. **To install the browser plugin for Firefox it's best you link to the plugin in the /opt/java/plugin/i386/ns7/ directory (in the Opera browser you can manually select the Java path via the settings section).
```
sudo ln -s /opt/java/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla/plugins
```

This should have created a symbolic link in the /usr/lib/mozilla/plugins directory. Restart Firefox (and make sure Java is enabled **Go to Edit > Preferences. Under Advanced category > Select Enable Java**) and test it out at: [http://www.java.com/en/download/installed.jsp?detect=jre&try=1](http://www.java.com/en/download/installed.jsp?detect=jre&try=1)

To enable Java system-wide you'll have to add the directories to the PATH variable. Create a new shell file as root (e.g. java.sh), add the below lines to the file and save it in the "/etc/profile.d" directory.
```
PATH=$PATH:/opt/java/bin
export PATH
```

[COLOR="YellowGreen"]Next time you want to upgrade Java you just have to remove the existing Java directory
```
sudo rm -r /opt/java
```

And repeat steps 1 to 5.[/COLOR]

---

### Post by Pinon on 2009-06-20
Thank you very much for helping out so much EarthMind.

But is it missing a commando at step 3 at the list you posted, between the command "sudo" and the file (here being jre-6u14-linux-i586.bin)? 

---> sudo /path/to/file/the_java_install_file.bin

I am getting the following result when trying:

[step 2] johnny@birgit-laptop:~/0$ chmod a+x jre-6u14-linux-i586.bin
[step 3] johnny@birgit-laptop:~/0$ sudo jre-6u14-linux-i586.bin
sudo: jre-6u14-linux-i586.bin: command not found
johnny@birgit-laptop:~/0$ 

The jre-6u14-linux-i586.bin file being in the folder named "0".


Again, this list will help me out, so thank you for posting it. I just encountered an unexpected obstacle :p

---

### Post by michy99 on 2009-06-20
You need to put a ./ in front of the command.```
sudo ./jre-6u14-linux-i586.bin
```

Wouldn't it be easier to install java from Synaptic?

Edit: Never mind, I see you are installing 6-14 and the version in Synaptic is 6-13.

---

### Post by Pinon on 2009-06-20
Oh, a just a little dot missing here, lol! Seemingly so little, yet it means so much. Mama!

---

### Post by Pinon on 2009-06-20
Ok, the packages was succesfully unpacked.

Last lines from terminal, if of any interest of all is: 

"Creating jre1.6.0_14/lib/deploy.jar
 
Done."



Above step 4 of the list: 

Quote: "This should've created the /opt/java/jre1.6.0_<version> directory."

But it made no directory nor files inside the directory (home)/opt/java/ 

By the way, my /opt/java directories I have created at my home folder or home directory, like in: johnny@birgit-laptop:~/opt/java$. Was this wrong?

---

### Post by EarthMind on 2009-06-21
Don't put a dit "." in front of it (that would be the right way to execute a file in the directory you're currently in but not in our case). Step 1 told you to browse to the folder where you want to install Java, in my example /opt/java. 
So perform step 1 and then run the Java file by using the full **path** to the file. For example:
```
sudo /home/johnny/0/jre-6u14-linux-i586.bin
```

Follow my steps perfectly and it'll work.

[COLOR="Red"]If you would've executed the Java installation in the "0" folder it would install Java in the same folder and that's not what we want.[/COLOR]

After successful installation you can delete all the Java files in your home folder, i.e. /(home)/opt/java, /(home)/0 and the jre installation file.

---

### Post by Pinon on 2009-06-21
Thank you! Step 3 worked fine, I just had to follow your instructions closely ;) 

So the jre1.6.0_14 directory is installed within the "0" directory.

But I am still missing something here.

---> 4. Now copy the files to the /opt/java directory
Code:

sudo cp -R /opt/java/jre1.

I type from within /opt/java directory and get the result:

"johnny@birgit-laptop:~/opt/java$ sudo cp -R /opt/java/jre1.
cp: missing destination file operand after `/opt/java/jre1.'
Try `cp --help' for more information.
johnny@birgit-laptop:~/opt/java$ "

I am not sure what I did wrong here: "cp: missing destination file operand after `/opt/java/jre1.'"

---

### Post by EarthMind on 2009-06-21
I've updated my instructions with your file and folder names.

> So the jre1.6.0_14 directory is installed within the "0" directory.

No, remove that directory and everything else in your home folder that was created by the Java installation and let's start all over because we are trying to install it in the /opt/java directory.

Now, perform steps 1 to 6 in the right order **_including step 1_** which is the most important one.

---

### Post by Pinon on 2009-06-21
Thank you for all your effort to help me out here, mate! 

My mistake, when I said the jre1.6.0_14 directory is installed within the "0" directory, that was not what I meant. My brain!! Of course I meant I had created the /opt/java/jre1.6.0_14 directory.

Anyways, I removed that directory (the 0) and everything else (ex /opt/java) in my home folder that was created by the Java installation, and started over again.

Step 1 to 3 was successful. 

After step 3 the /opt/java/jre1.6.0_14 directory was created. 

Like this:

johnny@birgit-laptop:~/opt/java$ dir
jre1.6.0_14

Step 4: 

sudo cp -R /opt/java/jre1.6.0_14 /opt/java

Result:

johnny@birgit-laptop:~/opt/java$ sudo cp -R /opt/java/jre1.6.0_14 /opt/java
cp: cannot stat `/opt/java/jre1.6.0_14': No such file or directory
johnny@birgit-laptop:~/opt/java$ 


Sorry, I still can't get through step 4...

---

### Post by EarthMind on 2009-06-22
My mistake, I forgot the asterisk. This is the right command for step 4:
```
sudo cp -R /opt/java/jre1.6.0_14/* /opt/java
```

---

### Post by Pinon on 2009-06-22
I type:

sudo cp -R /opt/java/jre1.6.0_14/* /opt/java

Result:

johnny@birgit-laptop:~/opt/java$ sudo cp -R /opt/java/jre1.6.0_14/* /opt/java
cp: cannot stat `/opt/java/jre1.6.0_14/*': No such file or directory
johnny@birgit-laptop:~/opt/java$ 


jre1.6.0_14 is within opt/java directory:

johnny@birgit-laptop:~/opt/java$ dir
jre1.6.0_14

Content of jre1.6.0_14:

johnny@birgit-laptop:~/opt/java/jre1.6.0_14$ dir
bin	   javaws  LICENSE  plugin  THIRDPARTYLICENSEREADME.txt
COPYRIGHT  lib	   man	    README  Welcome.html
johnny@birgit-laptop:~/opt/java/jre1.6.0_14$

---

### Post by EarthMind on 2009-06-22
That's because you've installed Java in your home directory (~/opt/java/jre1.6.0_14) instead of in "/opt/java". Remove it with "rm -r /home/your_user/opt/java/jre1.6.0_14" and install it in "/opt/java". This is what step 1 does: create the directory "/opt/java" with the command "sudo mkdir /opt/java" and browse to that directory "cd /opt/java".

Installing Java in your home directory isn't bad but it's not recommended either, you better install it in a root-only place such as "/opt/java".

I've also added how to enable Java system-wide by configuring the PATH variable.

---

### Post by Pinon on 2009-06-22
Ok!

But it won't work here, that is why I (sorry) installed it at wrong place.

Here is what is happening at step 1:

johnny@birgit-laptop:~$ sudo mkdir /opt/java
mkdir: cannot create directory `/opt/java': No such file or directory

It is not meant to be THAT easy, is it?

---

### Post by EarthMind on 2009-06-22
Why can't it create a directory? Doesn't it give any more info? And can you "cd /opt/java"?

---

### Post by Pinon on 2009-06-22
No, it does not give any more information. And I can't "cd /opt/java". (No such file or directory.)

I have no clue why I can't make that directory.

---

### Post by Pinon on 2009-06-23
It is solved!

At step 1:

In stead of "sudo mkdir /opt/java" I had to make 2 steps:

sudo mkdir /opt
cd /opt
sudo mkdir java
cd java


At java.com the java test now sais:
"Verified Java Version
Congratulations!
You have the recommended Java installed (Version 6 Update 14)."


Thank you for all your help and guidance EarthMind!

---

### Post by EarthMind on 2009-06-23
That's great :)! Have you also configured Java system-wide by creating the shell file? Some software will need this.

---

### Post by Pinon on 2009-06-23
No, I did not manage to make java system wide.

The option to make new files and directories are turned off inside that folder. (I used the file manager.) I don't know how to use the Terminal to create the file.

I tried to move the file into that directory, but the system reports that access is denied.

---

### Post by EarthMind on 2009-06-23
Open a terminal and type "sudo gedit", press enter and now you can create a file with root privileges :)

---

### Post by Pinon on 2009-06-23
Done. Or at least I guess it is system wide now. The file is now placed at its right location :)

---

### Post by EarthMind on 2009-06-23
Yay, enjoy your fresh new updated JRE :)

---

### Post by Pinon on 2009-06-23
Thank you for your patience and guidance mate!

I got Java system wide, thanks to you :popcorn::popcorn:

---

