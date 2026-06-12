---
title: "Did Enemy Territory infect my computer? How can I be sure?"
date: 2008-06-19
forum: Gaming &amp; Leisure
---

### Post by Sarah L on 2008-06-19
I just installed Wolfenstein: Enemy Territory today using the binary installer & patch from idsoftware.com. I played online for several hours and connected to quite a few game servers, many of which downloaded ~50mB EACH of maps and mod files to my home directory.

Is it possible that there could have been an exploit delivered to my computer either during the download stage or the gameplay stage? Just as an example, I can envision an attack taking place in the following steps:

1. client downloads malicious code from the server in the guise of a game mod
2. mod is loaded by the game and the malicious code is run
3. a keylogger is loaded into the background as an invisible (or simply disguised) process
4. the keylogger records input of the admin password (used for sudo) and sends it back to server
5. remote user uses admin password to take control of computer

At the time of installation and gameplay, my computer was:
-logged into an admin-enabled account
-unprotected by a firewall

The admin password was typed in afterwards to install Guarddog (a firewall configuration tool), possibly exposing it to malicious software.

The game software was installed a directory with user privileges only, so the originally downloaded files from idsoftware (assumed to be secure) were vulnerable to any subsequently downloaded files from the game servers (possibly malicious).

I've now deleted the folder in which the game was installed along with the .etwolf configuration folder. However, all of the files in my home directory were open to change by the game software, including such items as the kde Autostart directory, which could be exploited to run malicious scripts at startup.


So... is it possible that some malicious agent compromised my computer? And what can I do to detect / reverse this?

---

### Post by Sarah L on 2008-06-19
This thread is neither a joke nor a parody. I am asking a very serious question and I would like to recieve a serious response.

I do hope, however, that your reply is a joke - these forums are for helping out users in need of support, and certainly not a place to be hurling around insults.

---

### Post by Sarah L on 2008-06-19
The titles are similar because the question was similar.
No need to get all upset about it.

I didn't expect to get trolled on a tech support forum.
First time for everything though.

---

### Post by isaacj87 on 2008-06-19
<snip>

@ Sarah:

More than likely you're fine. I just checked my comp, and all the *.pk3 files downloaded (maps and stuff) were on my comp locally. Meaning all of theme were in my Home Folder. Check on your comp and see if you have an ~/.etwolf folder. I can understand your reason for concern, but I think you're okay. :) If you're really paranoid (I know I am!), you can download ClamAV or rkhunter and run a scan on your comp, just to be sure.

I'm no virus expert and your questions do interest me. I guess we'll have to wait and see what others say.

---

### Post by K.Mandla on 2008-06-19
Temporarily closed for staff review.

---

### Post by K.Mandla on 2008-06-19
I've reopened the thread after pruning out some inappropriate replies. My apologies to other members if I edited your posts.

To Sarah, I doubt something like that would go unnoticed by other Linux users. And like isaacj87 mentions, downloaded maps and modifications are generally stored locally. 

Of course, any time you download something in a binary form you run the risk of someone else tinkering with the guts of your machine. So you have to consider the source of your downloads. Otherwise, it's probably unlikely that the situation you describe has occurred.

P.S.: I'm going to moving this to the gaming forum, since it primarily deals with a situation arising from a game. :)

---

### Post by diaa on 2008-06-19
I'd like to mention somethings that will make you feel safer:
1- maps are not executable code, they are not a program, just a set of images, sounds and files to describe how things should go.
2- the worst that could happen is a game crash, in case the map is corrupted or something.
3- If an exploit is available and it's possible to do the tricky buffer overflow and code execution exploits it could be really dangerous but this is unlikely to go unnoticed and you're still left with root protection, the code won't be able to do anything requiring root privileges.

I hope this helps.

---

### Post by cogadh on 2008-06-19
Unless you are running ET with administrator privileges, there is not much anything you downloaded through the client could actually do to your system. Linux is inherently much more secure than Windows and to date there has never been a virus or any other malware available in the wild that could propagate on Linux. In fact, last time I checked, there had only ever been 14 viruses written for Linux since 1991 and none of them ever spread beyond the initial infection system. That's not to say that someday someone won't come up with something that will do bad things to Linux, but the likelihood that you have encountered that new thing is extremely slim. If your interested in some details about Linux security, forum staff member [bodhi.zazen](http://ubuntuforums.org/member.php?u=89054) wrote an excellent post about it that I highly recommend you read:
[http://ubuntuforums.org/showthread.php?p=3088372](http://ubuntuforums.org/showthread.php?p=3088372)

---

### Post by RIchard James13 on 2008-06-20
> **Sarah L said:**
> 1. client downloads malicious code from the server in the guise of a game mod
2. mod is loaded by the game and the malicious code is run


Even though this is theoretically possible, the barriers against the intruder are very high. 

First separate maps from mods. If you where going to do this you need the computer game to execute your code. But computer game mods are run in a special language and are as separate from the operating system as Javascript on a web page is. They can't read and write to the filesystem, they can't execute other programs, they are stuck in a little simulator. The "technical" term for this is a sandbox.

Why would a game developer make sure that code is run in a sandbox? One reason is stability, you don't want a faulty mod to crash the computer. Another reason is it is easier to start off with limits to what the mod can do, then you add abilities, it is just easier to do it this way.

You don't want a mod to see the files in the users directory, you want the mod to be able to load the map files and texture files and model files from the game files. 

If you want to know more you should look at game modding. By learning how to modify a game you can see how limited the mod code actually is.

---

### Post by frodon on 2008-06-20
My best security advice is to unplug your ethernet cable, as long as you have the cable plugged in the risk exists.
The rest is in your mind, there's not more risk using ET than with any other apps that use internet, the risk is just the same.

---

### Post by dislexic_one on 2008-06-20
It's funny this came up as just as last night, I had to reformat and install Ubunutu on our family pc due to an infected Counter Strike server downloading infected files.

It may sound improbable, but it has happened twice.  Think about it, especially on windows, you've given the program rights to download and "execute" foreign files.  A virus could easily be embedded into the file so that when CS runs it, boom! you're infected.

For linux though, I think you are safe, since script kiddies do not know anything else than windows.  I would follow one of the replies where if you are feeling paranoid, install ClamAV.

:)

---

### Post by cogadh on 2008-06-20
That seems quite unlikely, if not impossible, since the files you download from the game servers are not actually executable code at all, but simply readable data. It is far more likely that you got an infection from somewhere else, did not clean it completely, then reinfected yourself.

---

### Post by wootah on 2008-06-20
> **Sarah L said:**
> This thread is neither a joke nor a parody. I am asking a very serious question and I would like to recieve a serious response.

I do hope, however, that your reply is a joke - these forums are for helping out users in need of support, and certainly not a place to be hurling around insults.

Seriously? She asked a legit question and some one decided to insult her? :sad:

Well I'm glad the rest of this thread was kind enough to help her.

---

### Post by cogadh on 2008-06-20
Yeah, pretty surprising, huh? People around here are ususally much better behaved than that. Fortunately the mods dealt with it rather quickly and decisively.

---

### Post by wootah on 2008-06-20
> **cogadh said:**
> Yeah, pretty surprising, huh? People around here are ususally much better behaved than that. Fortunately the mods dealt with it rather quickly and decisively.

Mods get a +1 :)

---

### Post by isaacj87 on 2008-06-20
> **wootah said:**
> Seriously? She asked a legit question and some one decided to insult her? :sad:

Well I'm glad the rest of this thread was kind enough to help her.

Yeah, it was pretty ridiculous. Obviously, the mod erased the unkind words that the guy said from my post (I quoted him). I just hope the OP won't get scared off because I think it's safe to say the rest of us do not behave in such a way. :D

---

### Post by RIchard James13 on 2008-06-22
> **dislexic_one said:**
> It's funny this came up as just as last night, I had to reformat and install Ubunutu on our family pc due to an infected Counter Strike server downloading infected files.

It may sound improbable, but it has happened twice.  Think about it, especially on windows, you've given the program rights to download and "execute" foreign files.  A virus could easily be embedded into the file so that when CS runs it, boom! you're infected.

I just want to reinforce this point. Imagine that someone goes into a room and out comes a chicken. Does that mean the person turned into a chicken? With infections being so easy in Windows and detection lagging it is possible to think that because you detected the infection after a program ran that that program was responsible. When in reality it was a program that ran before it. If you have more evidence that this really happened than I noticed my computer was infected after I played CS please feel free to point it out. Otherwise you are just scaremongering.

---

### Post by ProbablyX on 2008-06-26
I agree. I see no way that Counter-Strike could have been distributing infected files.
AFAIK a normal server over the HL1 engine can only distribute maps and sound files (and limited scripting to play these sounds - like play the file "HIT!" after someone shoots for instance).

As said above all code is scripting, there are no binary data, unless you get a mod downloaded from a separate website (where they might have customized a custom program to run the game in).

To return to Enemy Territory; the game runs on both Windows, Mac and Linux computers. The server can only distribute scripts, as if a binary file was being sent out for Linux the Mac and Windows players' clients would get very confused.

---

