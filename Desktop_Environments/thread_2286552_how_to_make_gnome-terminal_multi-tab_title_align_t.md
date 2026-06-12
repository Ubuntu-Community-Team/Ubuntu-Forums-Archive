---
title: "how to make gnome-terminal multi-tab title align to left"
date: 2015-07-13
forum: Desktop Environments
---

### Post by chenzhiwei2 on 2015-07-13
[LEFT][COLOR=#222222][FONT=Helvetica Neue]After upgrading to Ubuntu 15.04, the Gnome Terminal tab title is set to the tab center. I really very dislike to set the title to the center of the window or tab.[/FONT][/COLOR][COLOR=#222222][FONT=Helvetica Neue]I tried with gtk.css but without luck. I also tried to find solution through Google, but still no luck.
[/FONT][/COLOR][COLOR=#222222][FONT=Helvetica Neue]Does anyone know how to change the title align to left?

[IMG]http://i.stack.imgur.com/pIRny.png[/IMG]

I also asked this question on AskUbuntu and StackOverflow:

[http://askubuntu.com/questions/620061/gnome-terminal-multi-tab-title-position](http://askubuntu.com/questions/620061/gnome-terminal-multi-tab-title-position)
[http://stackoverflow.com/questions/30905176/how-to-make-gnome-terminal-multi-tab-title-align-to-left](http://stackoverflow.com/questions/30905176/how-to-make-gnome-terminal-multi-tab-title-align-to-left)

Thanks.
[/FONT][/COLOR][/LEFT]

---

### Post by chenzhiwei2 on 2015-07-20
Hello, any answers?

Thanks.

---

### Post by chenzhiwei2 on 2015-07-23
Let me answer my question.

1. Download the gnome-terminal source package

$ apt-get source gnome-terminal

2. Install the build requires

$ sudo apt-get install build-dep gnome-terminal

3. Rollback the change below

[https://github.com/GNOME/gnome-terminal/commit/468a18f5e21b42ee0efedf3d86203fbc4e02807e](https://github.com/GNOME/gnome-terminal/commit/468a18f5e21b42ee0efedf3d86203fbc4e02807e)

4. Repackage the source code

$ tar zcf gnome-terminal_3.14.2.orig.tar.gz gnome-terminal-3.14.2

5. Build new gnome-terminal package

$ debuild -b

6. Install the new gnome-terminal package

$ sudo dpkg -i gnome-terminal_xxx.deb

---

