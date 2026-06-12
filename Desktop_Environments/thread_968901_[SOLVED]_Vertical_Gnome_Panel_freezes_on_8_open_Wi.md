---
title: "[SOLVED] Vertical Gnome Panel freezes on 8 open Windows"
date: 2008-11-03
forum: Desktop Environments
---

### Post by Kyront on 2008-11-03
As described in [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/187540](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/187540) this is a long-standing bug with the gnome-panel desktop bar that occurs if you want to put it on the left or right side and open more than 7 windows.

It has been requested by Saïvann Carignan to move support over to the forums, so please read through the bug description in the link above and come back here if you have something to add. Thanks.

**Update:**

I updated [the script]("http://dominiklang.ch/gnome-panel-fix") to include the option to lock the newly created packages so Synaptic doesn't nag you about updating them. Thanks paskma for suggesting this.

---

### Post by Kyront on 2008-11-03
[QUOTE=mike]
Hi Mr. Dominik Lang,

I right clicked on the desktop and created a new empty file, copied the text in [http://dominiklang.ch/gnome-panel-fix](http://dominiklang.ch/gnome-panel-fix) and pasted it there, saved it and renamed it as "gnome-panel-fix".

But when I opened a terminal, navigated to the desktop and ran "sudo gnome-panel-fix" , it said "command not found". ;-(

Would you kindly tell me what is wrong?

Thanks.
[/QUOTE]

As explained in the original post, you have to make it executable first. You can do this through [the file's settings panel]("http://ma65p.wordpress.com/2008/08/04/how-to-make-a-file-executable-in-ubuntu/") or with the command chmod in the shell. If you're in the Desktop folder, don't forget to use the current directory to run the script (./):

```

~/Desktop$ chmod u+x gnome-panel-fix
~/Desktop$ sudo ./gnome-panel-fix

```

---

### Post by donotaskwhoiam on 2008-11-03
Thank you very very much Mr. Dominik Lang, it works perfectly. You are brilliant!

By the way, the second command line should be "sudo ./gnome-panel-fix", not "./gnome-panel-fix". Maybe you just forgot it. ;-)

And I restarted my pc to make the change effective, and think so are you.

:-)

---

### Post by Kyront on 2008-11-03
> **donotaskwhoiam said:**
> Thank you very very much Mr. Dominik Lang, it works perfectly. You are brilliant!
You're welcome, but i have to hand those over to paskma, as he basically did all the coding. Shell scripting is "just" a series of programs to execute. :)

> **donotaskwhoiam said:**
> By the way, the second command line should be "sudo ./gnome-panel-fix", not "./gnome-panel-fix". Maybe you just forgot it. ;-)

And I restarted my pc to make the change effective, and think so are you.

:-)
Thanks for your feedback, i'll change the former and have a look at the latter. By the way, could you tell me the versions of your gnome-panel- and libwnck22-packages, so i can add those as having been tested? You can find them in Synaptic or get them by issuing these commands from the script:

```
$ dpkg -s gnome-panel | grep "Version:*" | grep -oE "[[:digit:]]\.[[:digit:]]+\.[[:digit:]]+"
$ dpkg -s libwnck22 | grep "Version:*" | grep -oE "[[:digit:]]\.[[:digit:]]+\.[[:digit:]]+"
```

Maybe you need sudo again for those. Little trick if it doesn't work without sudo: Try the following just after it complains about not having enough rights:
```
$ sudo !!
```
!! means: insert the last command here

---

### Post by donotaskwhoiam on 2008-11-04
i am using ubuntu 8.10 which is released few days ago, and gnome is 2.24.1, libwnck22 is 2.24.1 too.

thank  you.

---

### Post by dpstyles on 2008-11-09
Guys, Thanks for all your hard work on this one - Great fix.  Just to let you know that fakeroot must be installed prior to running the script / fix.  Also a tiny point, the last " appears to be missing from the script

---

### Post by cayhorstmann on 2008-11-10
Unfortunately, that patch doesn't solve the problem for me. It is the same as always. Icons get smaller and smaller; with the eighth icon, the flicker starts. 

I run Intrepid.

---

### Post by tow on 2008-11-11
I finally upgraded my primary machine to 7.10 over the weekend (hey, it just worked so if not broken...) and then started experiencing this problem. My panel is on the right of my screen and I stretched it so the icons would show up.  I was **very** unhappy! Googled until I found the bug report that Gnome seems to have disowned and requested be moved here...

I must say "paskma, you da man!".  I ran the script and all seems well. Made sure I could have more than 7 icons in the panel without it freezing (it was gobbling cpu and constantly grabbing more memory according to top).

I also answered 'y' to the question in the script about locking this version but now Update Manager always lists libpanel-applet2-0 and libwnck22 in the list of updates. The displayed versions in Update Manager are the same as are listed in Synaptic (both 2.20.1).  In Synaptic I manually locked the installed version so my questions are...

How do I get Update Manager to ignore these two packages?
Is this ever going to get permanently fixed?

tia.

---

### Post by Kyront on 2008-11-13
> **dpstyles said:**
> Guys, Thanks for all your hard work on this one - Great fix.  Just to let you know that fakeroot must be installed prior to running the script / fix.  Also a tiny point, the last " appears to be missing from the script
Thanks, i fixed the missing ", added a line to install the fakeroot package and also updated the script to prompt the user to log out of the gnome session so the gnome-panel can be restartet. This has been tested on my machine with gnome-panel2.24.1ubuntu2.1.


> **cayhorstmann said:**
> Unfortunately, that patch doesn't solve the problem for me. It is the same as always. Icons get smaller and smaller; with the eighth icon, the flicker starts. 

I run Intrepid.
Hm ok, some questions: Do you have a clean installation of 8.10 or is it an upgrade? Which versions of gnome-panel and libwnck22 do you have (see commands above)?

You could try to run the commands in the script individually and see if there's a problem with the patching of the files.


> **tow said:**
> The displayed versions in Update Manager are the same as are listed in Synaptic (both 2.20.1).  In Synaptic I manually locked the installed version so my questions are...

How do I get Update Manager to ignore these two packages?
Well actually, the "hold" commands should prevent the update manager from listing the packages, but i'm afraid i'm no expert on the matter. Maybe it's because those are not the base versions of your current release..

> **tow said:**
> Is this ever going to get permanently fixed?

tia.
Probably ;)

---

### Post by kpmeyer on 2008-12-20
I have this problem on a fresh install of 8.10.  I tried the upgrade of gnome-panel that the update manager suggested, but this didn't solve the problem.  My versions are as follows:


$ dpkg -s gnome-panel | grep "Version:*" | grep -oE "[[:digit:]]\.[[:digit:]]+\.[[:digit:]]+"
2.24.1

$ dpkg -s libwnck22 | grep "Version:*" | grep -oE "[[:digit:]]\.[[:digit:]]+\.[[:digit:]]+"
2.24.1

My question is, now that a patch has been made available, how do we get this into the main build?

To answer my own question, I have gone to [the bug in launchpad]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/187540") and clicked 'nominate for release'.  Maybe that will raise the issue further up the chain of command.

---

### Post by Kyront on 2008-12-23
I've been digging a little bit deeper and had a look at the gnome bugtracker [here]("http://bugzilla.gnome.org/show_bug.cgi?id=513347") and then followed the [link brought up in comment #16]("http://bugzilla.gnome.org/show_bug.cgi?id=86382").

That bug has been open since 2002 and only recently seemed to be having a little bit of discussion in the tracker. The developers/maintainers/whoever seem to ignore the efforts made to provide fixes for the problem, so maybe they have some work of their own they don't want to overwrite? It's up to anyone's guess, but personally, i wouldn't hold my breath that this is being fixed anytime soon.

I can only help you if you've got a problem with the script. If you don't want to modify your installation i suggest you don't use vertical panels (sorry) or swith to another desktop environment, e.g. KDE.

---

### Post by uvdevnull on 2009-01-21
I was so looking forward to fixing this... 
I ran the script and it seems to have completed successfully. 
However, after a reboot, the problem persists :(
How can I check that the patch was successfully applied and that I'm running the patched code for the panel?

---

### Post by Kyront on 2009-01-22
I've just rerun the script to check if there was some change to the libraries that would break it. However for me, it's been working fine once again.

You can try to run the commands in the script one by one to see if there's a problem with patching the sources. Note that you'll have to prepend most of the commands with 'sudo'.

Most of the script consists of setting up your machine to be able to create your own packages. The two lines that need to work are the following:

```
patch -p0 < gnome-panel-paskma.patch
patch -p0 < libwnck-paskma.patch
```

You'll have to have a look at the commands' output and you can't really tell otherwise, since these patches do not create a package-version of their own.

---

### Post by mulvila on 2009-03-12
Did not work for me (2.6.24-23-generic)

Got following messages:
```

gnome-panel-paskma-changelog.patch
gnome-panel-paskma.patch
libwnck-paskma-chagnelog.patch
libwnck-paskma.patch
Käyttö: grep [VALITSIN]... HAKUKAAVA [TIEDOSTO]...
Yritä "grep --help" saadaksesi lisäohjeita.
./gnome-panel-fix: line 19: [[:digit:]]\.[[:digit:]]+\.[[:digit:]]+: command not found
Käyttö: grep [VALITSIN]... HAKUKAAVA [TIEDOSTO]...
Yritä "grep --help" saadaksesi lisäohjeita.
./gnome-panel-fix: line 21: [[:digit:]]\.[[:digit:]]+\.[[:digit:]]+: command not found
current gnome panel version: 
current libwnck version: 
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|=== modified file 'gnome-panel-/gnome-panel/panel-widget.c'
|--- gnome-panel-/gnome-panel/panel-widget.c	2008-06-29 16:48:18 +0000
|+++ gnome-panel-/gnome-panel/panel-widget.c	2008-06-29 16:59:28 +0000
--------------------------
File to patch: 

```

Any suggestions?

---

### Post by donotaskwhoiam on 2009-03-19
here is a bad news.

this problem exists in ubuntu9.04(still in alpha stage) with gnome 2.26 also.

The God cried, "I will not see this bug fixed before I die!"

---

### Post by sapmemailek on 2009-06-01
Thank you guys for the great work! 
The patch worked for me perfectly! 
 
I use Ubuntu Januty 9.04,  
gnome-panel version: 2.26.0  
libwnck version 2.26.0

And donotaskwhoiam - please exclude your comments like this:
> **donotaskwhoiam said:**
> The God cried, "I will not see this bug fixed before I die!"

---

### Post by sireel on 2009-06-20
Does anyone know if this patch and script still works in 9.04? if not, I'm willing to try it out if someone is willing to help me un-patch it on failiure :)

---

### Post by Malvolio on 2009-07-07
Is there a fix for Jaunty?  I've confirmed that this bug still exists in 9.04.

---

### Post by dynamics on 2009-10-19
Hi

Use the script in the following web page

[http://www.osfight.de/archives/92](http://www.osfight.de/archives/92)

Download the script and run the commands.

The down-gradation takes a long time but its worth a try.
Don't forget to lock the future update for panel.

You may find Yahoo! german to english translator useful

---

### Post by 3esmit on 2009-11-01
thank you for sharing this fix. worked for me.

---

### Post by thundre on 2010-02-23
I just want to note that this bug persists in Ubuntu 9.10.  

The gnome-panel-fix script still works too.  But it still only uses the top half of the app panel before it switches to icons that are half the panel width.

And one more thank-you for posting the fix!

---

### Post by jcsjcs on 2010-11-15
> **thundre said:**
> I just want to note that this bug persists in Ubuntu 9.10.  

The gnome-panel-fix script still works too.  But it still only uses the top half of the app panel before it switches to icons that are half the panel width.

And one more thank-you for posting the fix!

Just an update: this bug still persists in 10.10. At least one patch of gnome-panel-fix failed, but the result is still satisfactory.

JCS.

---

### Post by regiss on 2010-11-26
> **jcsjcs said:**
> Just an update: this bug still persists in 10.10. At least one patch of gnome-panel-fix failed, but the result is still satisfactory.

JCS.


Hi guys,
if you get error with repositories then try this

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv DB141E2302FDF932
sudo apt-get update

---

### Post by aditya.sharma on 2010-11-26
I was considering this but finally actually preferred getting this completely different gnome-panel applet called Talika rather than using the patch. It works pretty well actually, just putting it down here so that everyone is aware of this other option too:

[http://ubuntuforums.org/showpost.php?p=10166793&postcount=40](http://ubuntuforums.org/showpost.php?p=10166793&postcount=40)

---

