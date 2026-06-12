---
title: "Trying to get Minecraft 1.6.2 to work on Xubuntu 11.10"
date: 2013-08-28
forum: Gaming &amp; Leisure
---

### Post by IanTannir on 2013-08-28
I'm new here and am totally lost so please have mercy on my naivety

My problem is that I cannot get Minecraft to run of course and I've tried multiple ways by the use of the Terminal. Doesn't work. So what I do instead is this: 

I go to my Downloads Folder in File Manager and find Minecraft.jar which I've downloaded I don't know how many times.

Then I right click on it and click the pop up option : Open with Open JDK Java 6 Runtime.

A message pops up saying as follows - The file '/home/user/Downloads/Minecraft.jar' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

How do I make this file executable? 

Mind you I've already tried the bit about going into the Permissions and clicking the little button which apparently makes Minecraft.jar executable. Problem is no such option exists in Xubuntu but does in Ubuntu.

I've been trying to solve this problem for days and it's really been giving me a headache. Can someone give me some help?

Much Obliged,

Ian

---

### Post by IanTannir on 2013-08-28
I will be updating to Version 12.04 soon by the way. Will that change anything in regards to getting Minecraft.jar to work?

---

### Post by TenPlus1 on 2013-08-29
First you have to install a few libraries, so in Terminal type this line:

sudo apt-get install liblwjgl-java 


Then follow this guide on how to install and set it up properly in Ubuntu: [http://www.wikihow.com/Play-Minecraft-in-Ubuntu](http://www.wikihow.com/Play-Minecraft-in-Ubuntu)

---

### Post by reavesjz on 2013-08-29
I'm not terribly familiar with the subtle nuances of Xubuntu, but on Ubuntu (Using Nautilus) you would **right-click** [COLOR=#006400]Minecraft.jar[/COLOR], select the **Properties** option. On the resulting window, select the **Permissions** tab at the top, and check the "**Allow executing file as program**" is allowed (make sure it isnt a [COLOR=#ff0000]**-**[/COLOR] sign). Personally, mine isn't ticked. But I'm using Ubuntu 13.04, and the Oracle Java7 environment. I hope this helps you out!

---

### Post by William_Correia on 2013-08-29
Since the little option in the GUI is not letting you change the permissions of the jar, you could try doing so via the terminal.  The wikipedia page may help, but you should be able to simply use "chmod u=rwx minecraft.jar"  This sets the owner of the file to have read, write, and execute permissions.

Heres the wiki page if you need it: [http://en.wikipedia.org/wiki/Chmod#Symbolic_modes](http://en.wikipedia.org/wiki/Chmod#Symbolic_modes)

---

### Post by IanTannir on 2013-08-30
> **William_Correia said:**
> Since the little option in the GUI is not letting you change the permissions of the jar, you could try doing so via the terminal.  The wikipedia page may help, but you should be able to simply use "chmod u=rwx minecraft.jar"  This sets the owner of the file to have read, write, and execute permissions.

Heres the wiki page if you need it: [http://en.wikipedia.org/wiki/Chmod#Symbolic_modes](http://en.wikipedia.org/wiki/Chmod#Symbolic_modes)

The response I got from the terminal was simply: "cannot access 'minecraft.jar' no such file or directory'

The odd thing is Minecraft.jar is in my downloads and documents.

All your responses are helpful with Ubuntu and Ubuntu only. I'm using Xubuntu a combination of Xfce and Ubuntu (no idea why I'm using Xubuntu anyway, my brother set it up) 

and I'd like to know how to run Minecraft.jar on Xubuntu not Ubuntu. Thanks for your advice but sadly none of it was 

helpful as nothing any of you contributed works. What I meant to say about the options button to set Minecraft.jar to an 

executable file is this : There is no such option in Permissions.

-Ian

---

### Post by whatthefunk on 2013-08-30
In a terminal you need to type:
chmod +x FULL_FILE_NAME

---

### Post by IanTannir on 2013-08-30
> **whatthefunk said:**
> In a terminal you need to type:
chmod +x FULL_FILE_NAME

I did chmod +x minecraft.jar

I got "could not access 'minecraft.jar' no such file or directory."

---

### Post by IanTannir on 2013-08-31
Another issue.
Whenever I do any other command in Terminal besides java -jar minecraft.jar I consistently recieve the message "cannot access minecraft.jar no such file or directory". How can I fix this?

Thanks,

Ian

---

### Post by reavesjz on 2013-08-31
I know what I'm about to ask will seem simple and useless, but let's make sure the basics are covered before this is delved in much further.
Just before you would normally type *java -jar Minecraft.jar*, type *ls* instead (LS, lowercase). Does it show Minecraft.jar as one of the files? If so, continue to type *java -jar Mine*, then hit tab, and see if it autocompletes the filename. If *ls* showed the file, and it autocompleted, then there is definitely something wrong here (Not that I'm doubting the issue, just without being in front of the machine it is difficult to see things like this).

---

### Post by whatthefunk on 2013-08-31
Are you using minecraft.jar or Minecraft.jar?  On my system, the M is a capital M.

---

### Post by DarkAmbient on 2013-09-01
The launcher for 1.6.2 comes with a capital M, for some reason.

```
sudo apt-get install openjdk-7-jre
```
```
wget [https://s3.amazonaws.com/Minecraft.Download/launcher/Minecraft.jar](https://s3.amazonaws.com/Minecraft.Download/launcher/Minecraft.jar)
```

If you plan on launching MInecraft without terminal, first do:
```
chmod +x Minecraft.jar
```
Then rightclick Minecraft.jar, properties then set to start with openjdk as default, then doubleclick Minecraft.jar

Or starting with  terminal:
```
java -jar Minecraft.jar
```

---

