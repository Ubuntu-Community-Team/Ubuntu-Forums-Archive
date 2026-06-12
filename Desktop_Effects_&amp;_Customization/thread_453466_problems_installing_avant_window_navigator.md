---
title: "problems installing avant window navigator"
date: 2007-05-24
forum: Desktop Effects &amp; Customization
---

### Post by rootkowski on 2007-05-24
Hello!

I'm trying to install the avant dock from a tar.gz on my feisty 64-bit and it isn't working. I'm quite new to linux so perhaps I do something wrong. Anyway this is what i do:
I cd into the extracted folder and then run the following command:
[INDENT][FONT="Courier New"]./autogen.sh --prefix=/usr && make && make install[/FONT][/INDENT]

The command comes from the readme file included with the tar.

Everything goes fine until the very end of the installation where I just get this: 
[INDENT][FONT="Courier New"]make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.[/FONT][/INDENT]

I don't know what that means. And I don't know how to fix it. I tried running the same command as sudo too, no help there.

I'll be very greatful for any ideas. Thanks a lot!

---

### Post by reacocard on 2007-05-24
That's normal. make install must be done with sudo, but aside from that, it all looks fine.

Here's the most current guide to installing AWN: [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

---

### Post by rootkowski on 2007-05-24
Thank you a lot for your response. I tried and unfortuantely it didn't help. I must have messed up something properly. I can't start the avant, neither the settings for it. when i tried to run it from the terminal this is what i got:

[INDENT][FONT="Courier New"][SIZE="2"]przemek@ubuntu:~$ avant-window-navigator
Segmentation fault (core dumped)[/SIZE][/FONT][/INDENT]

I'll try to find something but Id appriciate some more help. Thanks again!

EDIT:
I also tried to run avant preferences from the terminal and this is what I got:

[FONT="Courier New"][SIZE="2"][INDENT]przemek@ubuntu:~$ avant-preferences
/usr/local/share/avant-window-navigator/window.glade
Traceback (most recent call last):
  File "/usr/local/bin/avant-preferences", line 250, in <module>
    app = main()
  File "/usr/local/bin/avant-preferences", line 143, in __init__
    self.setup_chooser(APP_ACTIVE_PNG, self.wTree.get_widget("activefilechooser"))
  File "/usr/local/bin/avant-preferences", line 221, in setup_chooser
    chooser.set_filename(self.client.get_string(key))
TypeError: GtkFileChooser.set_filename() argument 1 must be string, not None[/INDENT][/SIZE][/FONT]

Any help? Anyone?

---

### Post by Jilbert on 2007-05-29
Am getting this error. what will I do next?

You need to install the gnome-common module and make
sure the gnome-autogen.sh script is in your $PATH.

thanks in advance. :)

---

### Post by rootkowski on 2007-05-29
I guess that if you run ubuntu you do have gnome-common module. 

What command are you running to execute the script? According to the readme file in the avant archive you are supposed to do the following (you are supposed to execute the commands in the folder to which avant was  extracted):

[INDENT][FONT="Courier New"][SIZE="2"]./autogen.sh --prefix=/usr && make && make install[/SIZE][/FONT][/INDENT]

Though I would suggest you do one at a time, meaning:

[INDENT][SIZE="2"][FONT="Courier New"]./autogen.sh --prefix=/usr[/FONT][/SIZE][/INDENT]

then

[FONT="Courier New"][SIZE="2"][INDENT]make[/INDENT][/SIZE][/FONT]

and then

[FONT="Courier New"][SIZE="2"][INDENT]sudo make install[/INDENT][/SIZE][/FONT]

I hope it will work for you :-)

---

### Post by rootkowski on 2007-05-29
I just managed to install avant on my system! :-D How? Previously I was trying to install it from source. This time, after deleting all stuff connected with avant, I downloaded an .rpm for fedora x64 and converted it to .deb using alien. (I run 64-bit feisty) The conversion went smoothly and then I just clicked on the newly made .deb, the package manager installed it and now it runs without problems. Nice, huh! :popcorn:

---

