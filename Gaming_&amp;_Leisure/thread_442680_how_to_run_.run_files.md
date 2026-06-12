---
title: "how to run .run files?"
date: 2007-05-13
forum: Gaming &amp; Leisure
---

### Post by voidoid on 2007-05-13
Hi, I'm attempting to install doom3 three onto fiesty, but don't know how to run the .run file they tell you to use here [http://zerowing.idsoftware.com/linux/doom/]("http://zerowing.idsoftware.com/linux/doom/")

can someone guide me through this step by step please, I've been using windows to long to anything useful!

---

### Post by deanjm1963 on 2007-05-13
type 

sudo sh nameoffile.run

hit enter, it should ask for your password and it should install.

hope this helps.

---

### Post by voidoid on 2007-05-14
Not working it jsut tells me that

sh: Can't open doom3-linux-1.3.1.1304.x86.run

---

### Post by noerrorsfound on 2007-05-14
> **voidoid said:**
> Not working it jsut tells me that

sh: Can't open doom3-linux-1.3.1.1304.x86.run
That means it can't find the file. You probably have not changed directory to where the file is located or did not include the full path in the command provided by deanjm1963.

By default the console is always at your home directory (/home/yourusername). If the file is on your Desktop, first type *cd ~/Desktop* (~ is a shortcut you can use instead of typing /home/yourusername) and then run the command, or just run the command with the full path:
```
sudo sh ~/Desktop/doom3-linux-1.3.1.1304.x86.run
```

---

### Post by weblordpepe on 2007-05-14
dont you just type:
```
./filename.run
```

---

### Post by lakersforce on 2007-05-14
You have to make the .run file executeable. Right-click, select properties and check "executeable".

---

### Post by sunaruni on 2008-05-06
I'm having the same problem trying to install my video driver from ATI.. I've checked to run it as executable, but it says I need to run it as super-user. How do I do that?

---

### Post by Saint Angeles on 2008-05-06
> **sunaruni said:**
> I'm having the same problem trying to install my video driver from ATI.. I've checked to run it as executable, but it says I need to run it as super-user. How do I do that?
sudo sh ati...

---

### Post by sunaruni on 2008-05-06
> **Saint Angeles said:**
> sudo sh ati...

I do that and it says it can't open the file. I'll try again now that I've checked the exe box..

---

### Post by sunaruni on 2008-05-06
No, it still can't open the file. I've tried typing in the full address and then just the filename.. it gives me ```
sh: can't open /home/joel/desktop/ati-driver-installer-8-4-x86.x86_64.run
or
sh: can't open ati-driver-installer-8-4-x86.x86_64.run
``` It's weird as hell.

---

### Post by Saint Angeles on 2008-05-06
> **sunaruni said:**
> I do that and it says it can't open the file. I'll try again now that I've checked the exe box..
ive downloaded the fglrx about a million times and everytime, i just navigate to the directory and sudo sh ati[tab]... theres no need for check boxes and exe and the like...

---

### Post by sunaruni on 2008-05-06
Do you mean literally typing "ati" or are you just using that as a filler for the filename?

---

### Post by sunaruni on 2008-05-06
Because nothing is working, and I want to try everything.. I just want to play a game or two.. or at least have vid. support to watch a fecking video online.

---

### Post by inportb on 2008-05-06
> **sunaruni said:**
> No, it still can't open the file. I've tried typing in the full address and then just the filename.. it gives me ```
sh: can't open /home/joel/desktop/ati-driver-installer-8-4-x86.x86_64.run
or
sh: can't open ati-driver-installer-8-4-x86.x86_64.run
``` It's weird as hell.

Have you tried making the file executable?

chmod +x ati...

EDIT: oops, didn't read that you had. rofl.

---

### Post by sunaruni on 2008-05-06
Well, I've got it set up as an executable, and I renamed it just "atidriver.run" to simplify things a bit... When I run it (I get the option to run it in the terminal as well, but choosing just run) it opens up a folder filled with files on my desktop with it, and then when the "super-user" message comes up, the file disappears. I copied the folder last time it popped up thinking I could put it somewhere to get it to work.

---

### Post by Perfect Storm on 2008-05-06
```
[size=1]cd ~/Desktop
chmod +x ati-driver-installer-8-4-x86.x86_64.run
sudo ./ati-driver-installer-8-4-x86.x86_64.run
[/size]
```

Try that instead.

---

### Post by sunaruni on 2008-05-06
> **Artificial Intelligence said:**
> ```
[size=1]cd ~/Desktop
chmod +x ati-driver-installer-8-4-x86.x86_64.run
sudo ./ati-driver-installer-8-4-x86.x86_64.run
[/size]
```

Try that instead.

Thank you VERY much.. That got the installer running. Now, here's hoping it actually works this time. Usually I get the driver up and it gives me a blank screen after loading at boot.

---

### Post by sunaruni on 2008-05-06
Hmm.. It worked to install the Catalyst Control Center, at least. I can't open that because it won't acknowledge that I have the ATI driver installed. So I go into aticonfig, but I don't know what to do to get it set up, really. Help?

---

### Post by Perfect Storm on 2008-05-06
Have your checked: [http://ubuntuforums.org/showthread.php?t=515573&highlight=install+latest+ATI](http://ubuntuforums.org/showthread.php?t=515573&highlight=install+latest+ATI)

---

### Post by sunaruni on 2008-05-06
> **Artificial Intelligence said:**
> Have your checked: [http://ubuntuforums.org/showthread.php?t=515573&highlight=install+latest+ATI](http://ubuntuforums.org/showthread.php?t=515573&highlight=install+latest+ATI)

Yeah, I've got envy still on here. It gave me essentially the same driver that was with Ubuntu that didn't work. It gave me a blank screen after loading. But at least it actually got installed. This one still isn't really registering, I don't think. Know what I can do with aticonfig?

---

### Post by inportb on 2008-05-06
> **Artificial Intelligence said:**
> ```
[size=1]cd ~/Desktop
chmod +x ati-driver-installer-8-4-x86.x86_64.run
sudo ./ati-driver-installer-8-4-x86.x86_64.run
[/size]
```

Try that instead.

Ah... I guess it needs bash/dash. sh is not good enough?

---

### Post by sunaruni on 2008-05-06
Well, found a page saying how to get it to auto-config... gives me a black screen after load, every time. Had to revert to stock settings again.

It's starting to look like I won't ever get to use my driver correctly.

---

### Post by Perfect Storm on 2008-05-06
*A.I. goes mod mode*

I think you should start a new thread in the [http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334) about how to configure the ATI driver, you'll get better support for this kind of questions instead of posting in a not related already made thread.
With the right title and enough info in that thread should do it.

---

