---
title: "ooqstart-gnome not working"
date: 2006-03-01
forum: Desktop Environments
---

### Post by towsonu2003 on 2006-03-01
I was gonna file a bug, but I wanted to post this first. 

I apt-getted it, but it does not launch anything. as path to the application, I tried /usr/bin/openoffice ; /usr/bin/ooffice2 ; /usr/bin/oobase2 ; and /usr/bin/oowriter2 . Nothing happens when I click on 'new text', 'new sheet' and so on. the launch times of openoffice did not change either. 

I  also did sudo apt-get --purge remove ooqstart-gnome sudo apt-get clean sudo apt-get install ooqstart-gnome and sudo dpkg-reconfigure ooqstart-gnome. I also deleted .gnome2/ooqstart-gnome. none of these worked... 

any ideas? thanks

PS. I'm using the OOo2 version that came with ubuntu.

---

### Post by towsonu2003 on 2006-03-02
reported bug here: [https://launchpad.net/distros/ubuntu/+source/ooqstart/+bug/33425](https://launchpad.net/distros/ubuntu/+source/ooqstart/+bug/33425)

---

### Post by NoNo_231 on 2006-03-02
Why don't you install it via synaptic? Aren't any menus at the applicaiton>office? If you search the usr/bin/ dir you will find the command for openoffice. If they are not there they will not work. I have the OO-2.0.1 and I don't remember the names of the commands for openoffice. Check the usr/bin/. It is something like ooffice and somehting else.

---

### Post by towsonu2003 on 2006-03-02
[QUOTE=NoNo_231]Why don't you install it via synaptic?[/QUOTE]
that's what I initially did. didn't work.

[QUOTE=NoNo_231]Check the usr/bin/[/quote]
None of the stuff in /usr/bin related to OOo works with ooqstart-gnome for me.

PS. To find stuff related to OOo, type "oo" (no quotes) in terminal and double tab. it will show you the commands that start with oo, which mostly are OOo commands and located in /usr/bin

---

### Post by NoNo_231 on 2006-03-02
Also I have found something that could help you in compiling 
[B]
Dmake[/B] is a make utility similar to GNU make or the Workshop dmake.

This utility has an irregular syntax but is available for Linux, Solaris, and
Win32 and other platforms. This version of dmake is a modified version of the
original public domain dmake, and **is used to build OpenOffice.org**.

---

### Post by towsonu2003 on 2006-03-02
[QUOTE=NoNo_231]Also I have found something that could help you in compiling 
[B]
Dmake[/B] is a make utility similar to GNU make or the Workshop dmake.

This utility has an irregular syntax but is available for Linux, Solaris, and
Win32 and other platforms. This version of dmake is a modified version of the
original public domain dmake, and **is used to build OpenOffice.org**.[/QUOTE]
I'd prefer to make the apt-gettable ooqstart to work. My initial post was bad and confusing, I should edit it :)
thanks for the suggestion though.

edit: edited initial post

---

