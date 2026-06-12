---
title: "Patching Gnome2 Globalmenu"
date: 2011-03-09
forum: Desktop Environments
---

### Post by taidoka on 2011-03-09
Hi all,

I successfully installed above named applet using the ppa repository files for ubuntu 10.10.
After restarting the system twice the preferences menu showed up as well. So far, so good.

But what I'd like to have is the possibility that globalmenu **displays the Nautilus desktop menubar** when a window without GTK compatibility is active (like Firefox, OO etc.).

Well I found a [patch]("http://code.google.com/p/gnome2-globalmenu/issues/detail?id=619") (Issue 619) at code.google.com which would probably fit!
But I don't know how to apply it?

Googling around I found a few tutorials explaining the patch. But I've still got some issues to make clear:
- Where is the file to patch? What directories do I've to scan?

Is there anyone who knows?
Any suggestions?

Kind regards
taidoka

---

### Post by Frogs Hair on 2011-03-09
Weird , I downloaded the patch  and when I opened it in Gedit it works but when I close the file browser it stops . I'm wondering if it has to be copied and pasted to a folder ?  This only happened when I first opened it and no longer displays the Firefox Menu , only the Gnome applications .

---

### Post by Frogs Hair on 2011-03-09
The folder is in File System usr/lib see these links. This process may require installing Meld from the software center.There seems to be more to this than a copy and paste. I keep looking for something with step by step instructions.      
[http://ubuntuforums.org/showthread.php?t=1624005](http://ubuntuforums.org/showthread.php?t=1624005)
[http://linux.about.com/od/commands/l/blcmdl1_patch.htm](http://linux.about.com/od/commands/l/blcmdl1_patch.htm)

---

### Post by taidoka on 2011-03-09
> Weird , I downloaded the patch  and when I opened it in Gedit it works  but when I close the file browser it stops . I'm wondering if it has to  be copied and pasted to a folder ?  This only happened when I first  opened it and no longer displays the Firefox Menu , only the Gnome  applications .Well it should display a standard menu in case of active NON-GTK applications like Firefox.
So this is not what it was supposed to do. But it's funny...
Anyway, as I understand a diff file quotes de facto the difference between the original file and a patched one.
So if I want to patch the diff in a folder there should be a file it belongs to.
Your link shows another method than the one I tried ([http://www.scottro.net/qnd/qnd-diff-patch](http://www.scottro.net/qnd/qnd-diff-patch)).

---

### Post by taidoka on 2011-03-09
> The folder is in  File System usr/lib see these links. This process may require  installing Meld from the software center.There seems to be more to this  than a copy and paste. I keep looking for something with step by step  instructions.      
[http://ubuntuforums.org/showthread.php?t=1624005](http://ubuntuforums.org/showthread.php?t=1624005)
[http://linux.about.com/od/commands/l/blcmdl1_patch.htm](http://linux.about.com/od/commands/l/blcmdl1_patch.htm)




That'd be nice.
Thanks in advance.

---

### Post by taidoka on 2011-03-09
> **Frogs Hair said:**
> The folder is in File System usr/lib see these links. This process may require installing Meld from the software center.There seems to be more to this than a copy and paste. I keep looking for something with step by step instructions.      
[http://ubuntuforums.org/showthread.php?t=1624005](http://ubuntuforums.org/showthread.php?t=1624005)
[http://linux.about.com/od/commands/l/blcmdl1_patch.htm](http://linux.about.com/od/commands/l/blcmdl1_patch.htm)
Hello Frogs Hair,

thanks for advices. Here's a list of the items found in /usr/lib 'globalmenu':

GlobalMenu.PanelApplet
GlobalMenu_PanelApplet.server
libglobalmenu-gnome-panel.so
libglobalmen-plugin.so
libglobalmenu-server.so
libglobalmenu-server.so.3
libglobalmenu-server.so.3.0.0

I tried the patch in a seperate folder and this is the terminal output:
"patching file monitor.vala
Hunk #1 FAILED at 302.
1 out of 1 hunk FAILED -- saving rejects to file monitor.vala.rej"

He was creating two files, one named 'monitor.vala.org' and one 'monitor.vala.rej'
He seems to be looking for a file called 'monitor.vala.org'.

Unfortunately I can't find that file.
These are the files I found:
libvala-0.10.so.0
libvala-0.10.so.0.0.0
libvala-0.10-0.list 
evala-0.10-0.mtl5sums 
evala-0.10-0.postinst 
libvala-0.10-0.postrm 
libvala-0.10.shlibs
_racc_evalact-i.yaml 
text-x-vala.icon 
text-x-vala.svg 
text-x-vala.svg 
text-x-vala.svg 
text-x-vala.svg 
vala.lang 
vala-terminal.png 
vala-terminal.png 
x-vala.xml 

So far now.

---

### Post by taidoka on 2011-03-10
> Well, the first problem is that i wrote the patch against the then-current git version, so if you're using an actual release that may not work.

But it looks like there's been a couple revisions in git since i made the patch, so it might not apply cleanly if you use now-current git. I'll investigate this further when i have access to my development stuff again.I wrote an email to the programmer and this is what he/she wrote. I'll wait for his/her reply and then I'll post it here.

---

### Post by Frogs Hair on 2011-03-10
> **taidoka said:**
> I wrote an email to the programmer and this is what he wrote. I'll wait for his reply and then I'll post it here.

Thanks for taking the time , I guess the best answer is pending .;)

---

### Post by taidoka on 2011-04-06
Well after receiving the above quoted mail I was waiting and waiting. But nothing obvious happend.
But today - as I started my computer I had to update my system again - a different behavior appeared: at the moment I close a window the default nautilus menu will be displayed in the panel now. This is very useful and elegant because I needn't click the empty space to get that menu on the panel, right?
Non-gtk applications are still not replaced by a default menu but that's okay for me.
Thanks to the developers, they did a good job and I needn't patch anything :)

Have a nice day
taidoka

Edit: This feature only works after opening nautilus once manually. To avoid this misbehavior I added a command to the startup list to open my homefolder (with nautilus) automatically.  Now it works like a charme.

---

