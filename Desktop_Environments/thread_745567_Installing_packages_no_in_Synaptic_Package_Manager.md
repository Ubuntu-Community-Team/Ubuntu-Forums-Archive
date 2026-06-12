---
title: "Installing packages no in Synaptic Package Manager"
date: 2008-04-04
forum: Desktop Environments
---

### Post by leona on 2008-04-04
Hi there

A friend is using ["GIZMO"]("http://gizmo5.com/pc/products/desktop/")  and wants me to use it, its a sort of Skype (VOIP) thing.
But I can't find it in the package manager, I looked at the site and I see there is a Linux version.
So how do I go about having this package added to the repos?

I don't like the idea of installing this manually, as to be honest I don't feel confident enough as to what I'm doing!  Whether it will corrupt anything, this is the main reason why I like the package manager, it sorts it all out for you.

Any idea how I can get this installed on my machine?

Thank you.

---

### Post by benerivo on 2008-04-04
Manually installing a .deb file is easy ansd can be undone. What you want to download is this file...
[http://download.gizmo5.com/GizmoDownload/gizmo-project_3.1.0.79_libstdc++6_i386.deb](http://download.gizmo5.com/GizmoDownload/gizmo-project_3.1.0.79_libstdc++6_i386.deb)

To install, open a terminal window, and type```
sudo gdebi
```then type a space, and then drag this file in to the console window, then hit return.

---

### Post by kostkon on 2008-04-04
> **benerivo said:**
> Manually installing a .deb file is easy ansd can be undone. What you want to download is this file...
[http://download.gizmo5.com/GizmoDownload/gizmo-project_3.1.0.79_libstdc++6_i386.deb](http://download.gizmo5.com/GizmoDownload/gizmo-project_3.1.0.79_libstdc++6_i386.deb)

To install, open a terminal window, and type```
sudo gdebi
```then type a space, and then drag this file in to the console window, then hit return.

or simply, double click on the .deb file.

---

### Post by totfit on 2008-04-04
Even easier would be to just open with gdebi. Most deb packages now will open with gdebi by default by just clicking on the even.

---

### Post by eriqjaffe on 2008-04-04
Or, from the terminal, just navigate into the directory with the .deb file and
```
sudo dpkg -i name_of_the.deb
```
...then again, I like the terminal, so... :)

---

### Post by leona on 2008-04-05
Arr cool, thank you, but I've hit a snag, I'm using 64bit Ubuntu, the package is i386 ops, guess I'll have to rethink that, drat.
I'll email them and see if they do a 64bit version.
Thank you all for your help though, that's taught me something new :) I'd always thought that manual installs where 'dangerous' so I've steered clear of them.

---

### Post by kellemes on 2008-04-05
> **leona said:**
> Arr cool, thank you, but I've hit a snag, I'm using 64bit Ubuntu, the package is i386 ops, guess I'll have to rethink that, drat.
I'll email them and see if they do a 64bit version.
Thank you all for your help though, that's taught me something new :) I'd always thought that manual installs where 'dangerous' so I've steered clear of them.

Maybe some interesting links for you?
[http://www.thebristows.com/blog/ubuntu/gizmo-project-64bit-deb]("http://www.thebristows.com/blog/ubuntu/gizmo-project-64bit-deb")
[http://ubuntuforums.org/showthread.php?t=424924]("http://ubuntuforums.org/showthread.php?t=424924")

---

### Post by leona on 2008-04-05
Wow, thank you so much, excellent find.

Can you tell me why when I searched here for 'gizmo' that I came up with a big fat nothing, I got  "no matches found" :(  would seem that me and search engines don't get on.

---

### Post by leona on 2008-04-05
I've used the first meothod
> [http://www.thebristows.com/blog/ubuntu/gizmo-project-64bit-deb](http://www.thebristows.com/blog/ubuntu/gizmo-project-64bit-deb)
and its installed, but when I click on the menu option, nothing happens, how can I find out what has gone wrong?

---

### Post by kellemes on 2008-04-05
> **leona said:**
> I've used the first meothod

and its installed, but when I click on the menu option, nothing happens, how can I find out what has gone wrong?

I don't know anything about Gizmo to be honest.
In order to find out why an application doesn't function it can help to run it from the terminal, the terminal-output may be informative.. Or at least give some output you can feed some search engine. ;-)

---

### Post by leona on 2008-04-05
Oh ya, great idea, thanks.

Yes doing this showed that it was missing the library, hum which the script was supposed to fix, no matter found the commend to get the right symlink so did that and its all working now, thank you.

Just out of interest why can't it report these errors to the GUI rather than just not starting?

---

### Post by kellemes on 2008-04-05
> **leona said:**
> Just out of interest why can't it report these errors to the GUI rather than just not starting?

Well.. that's up to the developers, surely they can create code that will catch such errors and inform the user about it, but this means investing time they better use to prevent errors in the first place. ;-)
The bottom line is.. errors shouldn't occur.

---

