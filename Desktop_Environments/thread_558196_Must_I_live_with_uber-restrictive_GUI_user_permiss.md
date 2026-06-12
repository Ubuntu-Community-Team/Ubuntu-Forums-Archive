---
title: "Must I live with uber-restrictive GUI user permissions?"
date: 2007-09-23
forum: Desktop Environments
---

### Post by aletheianalex on 2007-09-23
I pop in on Linux every few years (back as far as 68k Apple-issue linux), install it and kick it around for a few weeks to see how things have progressed, and then eventually uninstall.   I am a Mac user and much of the desktop and GUI sting  Microsoft IMHO.... BUT... I am liking the Feisty flavor except for the occasional M.S. ques like pop up bubbles for updates and those sort of annoyances.

Anyway, here is the biggest annoyance for me in this version: I will preface this by stating that I am quite comfortable with the terminal BUT, why type when you can click and drag?  That was the original mantra of the GUI personal computer after all.  So is there any way to get rid of the fascist restrictions under the desktop GUI apart from logging-in/unlogging back and forth with the root user account OR typing everything into the terminal under super-user?  I have looked around on this and other forums, and any time someone suggests any modification of root privleges, they get shouted down or the thread gets quietly relocated into obscirity.

(This is just an example that I made up so don't jump up my nose about why I would want to do this or say "oh... well for GURB you can just go to synaptic and compile blah blah and swap the root  blah kernel blah and lilo is better anyway blah and you don't need that for your system...") Let's say that I want to modify my GRUB configuration under GUI.  What I would want to do is copy/paste the config file to the desktop, make a few copies with various changes, make notes of those changes in each file info, and swap them in and out by dragging and dropping the files into my boot/grub folder.  NOPE!  Can't do that.  BUT you can open the terminal and 'sudo' 'cp' 'mv' boot/grub/blah/blah/blah ...and take 10 times longer to do it.  

The point is that if it is something that you CAN do under the terminal under your current user... WHY would you lock the GUI out of doing it?  AGAIN, the GRUB example was just to "for instance" so don't lock in on that... this is a general question about how/why  the OS functions as it does.  It accomplishes nothing except make a task take more time and increase the chance of error as is the caveat of every command line system.  EXAMPLE: under OSX, you can do that type of thing under GUI, BUT with you just get a popup requiring the admin/root password, and in MacOS back into the 80's, you could pop open anything you wanted  under the GUI and resedit/hexedit to your heart's content without any interference from the OS.

SO... forgive if you will the tone of the post, but these are the issues that seem to earn ridicule and/or chastisement from the general community and it gets frustrating.  The question boils down to : why can't I' OPEN up this particularly CLOSED but would-be open-OS, and why the general ridicule of others who have suggested/asked the same thing?

---

### Post by Lord Illidan on 2007-09-23
> The point is that if it is something that you CAN do under the terminal under your current user... WHY would you lock the GUI out of doing it? AGAIN, the GRUB example was just to "for instance" so don't lock in on that... this is a general question about how/why the OS functions as it does. It accomplishes nothing except make a task take more time and increase the chance of error as is the caveat of every command line system. EXAMPLE: under OSX, you can do that type of thing under GUI, BUT with you just get a popup requiring the admin/root password, and in MacOS back into the 80's, you could pop open anything you wanted under the GUI and resedit/hexedit to your heart's content without any interference from the OS.

In the 80s there wasn't the security threat that we have today.

And, personally, I prefer it this way, as there is less chance of me b0rking my system. If you want it your way, just enable root login.

---

### Post by coffeecat on 2007-09-23
> **aletheianalex said:**
> So is there any way to get rid of the fascist restrictions under the desktop GUI apart from logging-in/unlogging back and forth with the root user account OR typing everything into the terminal under super-user? 

Of course there is! This is Linux. :)

Open a terminal, and type:

```
gksudo nautilus
```and a nautilus file-manager opens with root privileges, **after** you've given your password. If you like that, it's easy enough to add a panel launcher or menu entry with the same command to get a root nautilus. Then you won't have to use the terminal. :wink:

And if you want to do other GUI things as root and not involving Nautilus, there will be a way.

---

### Post by Lord Illidan on 2007-09-23
Or you can install nautilus-gksu from apt-get/synaptic

Will give you an entry in the context menu (right click in nautilus)

---

### Post by kerry_s on 2007-09-23
your popping in and out of linux is hindering your education.

root:
press> alt+f2 <type> gksu nautilus /

see no terminal

now if your wanting to remove the asking for password, for this you need the terminal, it's safer.

type> sudo visudo
change
%admin ALL=(ALL) ALL
to
%admin ALL=(ALL) NOPASSWD:

ctrl + x & y & enter to save

i would prefer something safer, like limiting it to certain app's that are gui only, for example:

%nautilus ALL=(root) NOPASSWD: /usr/bin/nautilus
you'll need to create a "nautilus" group(sudo addgroup nautilus) and add your user, but it won't open up your whole system and you can use root nautilus with out a password. much safer, but takes more time to setup.

---

### Post by kerry_s on 2007-09-23
wait, my bag i forgot i simplified it on mine.

sudo visudo

%nopasswd ALL=(root) NOPASSWD: /usr/bin/nautilus, /usr/bin/gedit

sudo addgroup nopasswd
gksudo gedit /etc/group
add you user to nopasswd group

when you want to add another application just add it to that sudoers line.

have fun, remember gui apps only, you don't want command line application having no password.

---

### Post by aletheianalex on 2007-09-23
> **Lord Illidan said:**
> ... If you want it your way, just enable root login.

Yep... that is the first thing that I do with any Linux install since you never know what the developers of a partucular distro will lock out out of.

[QUOTE=kerry_s]
your popping in and out of linux is hindering your education.

root:
press> alt+f2 <type> gksu nautilus /

see no terminal

now if your wanting to remove the asking for password, for this you need the terminal, it's safer.

type> sudo visudo
change
%admin ALL=(ALL) ALL
to
%admin ALL=(ALL) NOPASSWD:

ctrl + x & y & enter to save

i would prefer something safer, like limiting it to certain app's that are gui only, for example:

%nautilus ALL=(root) NOPASSWD: /usr/bin/nautilus
you'll need to create a "nautilus" group(sudo addgroup nautilus) and add your user, but it won't open up your whole system and you can use root nautilus with out a password. much safer, but takes more time to setup.[/QUOTE]

Excellent... how about a standard option to enable that without the finger-tapdancing?  FUBAR-ing a Linux install is no biggie since it takes about 20 minutes to get it back up and running again (as long as it does not scramble your boot disk when it goes down) and besides... many OS-es don't require user-interaction to scramble the system... they do that just fine by themselves ;)

I am honestly trying to give Ubuntu a chance... if I can purge the M.S. trappings and user restrictiond.  I gave up on v6, but heard so much buzz about 'Feisty' that I had to try it.  Honestly, I still prefer scratch compiles/builds and minimal/lightweight flavors of the various managers , but I find a "just works" linux install enticing.

Thanx for the help.

---

### Post by aysiu on 2007-09-23
> **aletheianalex said:**
> why the general ridicule of others who have suggested/asked the same thing? I don't see any ridicule. Don't believe me? Check out this thread:
[[IDEA] Automatic password request for system file editing or moving](http://ubuntuforums.org/showthread.php?t=409852)

---

