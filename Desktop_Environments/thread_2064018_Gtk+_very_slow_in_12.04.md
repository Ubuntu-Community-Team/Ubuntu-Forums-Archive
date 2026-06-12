---
title: "Gtk+ very slow in 12.04"
date: 2012-09-28
forum: Desktop Environments
---

### Post by tommh on 2012-09-28
After upgrading to 12.04LTS, I noticed that some of my Gtk+ applications  started to run much more sluggishly. To look into this, I took a simple  Gtkmm application, which does nothing more than add ~50 standard Gtk  widgets (labels, spin buttons, toggle buttons, etc.) into a window, with  a single callback that changes the label on a toggle button when it's  clicked on. 

This runs perfectly under Ubuntu 11.10 (Gtk+ version 3.2.0, Gtkmm  version 3.2.0). However, running it on the same computer with Ubuntu  12.04.1 (Gtk+ version 3.4.2, Gtkmm version 3.4.0) it runs annoyingly  slowly. For example, when I click on a button, there is a large fraction  of a second( ~400mS at a guess) delay before anything happens. Right  click menus on spin buttons also take about this long to appear after  clicking.

Is this a known issue with the newer version? 

Tom

---

### Post by zombifier25 on 2012-09-28
Actually you are the only person having the prolem AFAIK. I can't help with the problem, but upgrading is still a messy process in Ubuntu and it tends to mess things up.

---

### Post by tommh on 2012-09-28
Hmm, that's odd. It's not an upgrading issue since I've tried it on several different PCs, one of which was a clean install...

---

### Post by kio_http on 2012-09-28
I have this issue too on clean installs. I was just testing it and found it slow. I haven't found a fix and didn't bother to as I use KDE.

What graphics card do you have? Mine is a GMA 950.

---

### Post by TenPlus1 on 2012-09-28
On different systems I find that Gtk themes that use an animated prograss bar (the moving slanty lines) tends to slow applications down and set my cpu at a constant 3%, and switching to a simpler theme fixes everything without the animated progress bar...  Gtk3 themes are worse for this...

---

### Post by farwater on 2012-11-08
I had a similar problem too under XFCE. Solved it by enabling display compositing. So, my guess is that it's a problem with the Xorg driver. The one I'm using is nvidia v.295.40. You may try switching to vesa driver and see if it makes any difference (change the value of Driver parameter in the Device section of your /etc/X11/xorg.conf to "vesa").
I hope that helps.

Below are the results of gtkperf test Before/After compositing enabled:


GtkPerf 0.40 - 100 cycles of all tests:

GtkEntry - time:  0.01 / 0.03
**GtkComboBox - time:  1.23 /  0.70**
GtkComboBoxEntry - time:  1.18 / 0.62
**GtkSpinButton - time:  0.62 /  0.18**
G**tkProgressBar - time:  0.34 / 0.11**
**GtkToggleButton - time:  0.33 / 0.10**
[B]GtkCheckButton - time:  0.23 / 0.07
GtkRadioButton - time:  0.26 / 0.08[/B]
GtkTextView - Add text - time:  0.41/  0.36
GtkTextView - Scroll - time:  0.01 / 0.07
GtkDrawingArea - Lines - time:  0.26 /  0.22
GtkDrawingArea - Circles - time:  0.53 /  0.20
**GtkDrawingArea - Text - time:  6.11 /  2.77**
**GtkDrawingArea - Pixbufs - time:  0.40 /  0.19**
 --- 
[B]Total time: 11.94 / 5.70

[/B]

---

### Post by alex-x-med on 2013-10-23
I am having the same problem.
I have used this development machine for years with Ubuntu 8.04 and then Ubuntu 10.04 to develop and support an extensive medical application in PyGtk and Gtk and I noticed after installing Ubuntu 12.04 that my entire GTK application runs unacceptably slowly. 
Before 12.04 it ran very quickly. 
For example, simply changing a notebook tab to an alternate page and back can take as long as 20 seconds where on 10.04 and 8.04 it took less than 1 second.

---

### Post by alex-x-med on 2013-10-24
I found my problem.
I was using the incorrect NVidia driver for my video card and it was causing a number of issues.
After going in to System Tools -> System Settings -> Additional Drivers and choosing the recommended driver, my speed is back to normal.

---

### Post by alex-x-med on 2014-05-21
Actually, I am also having the problem, but the magnitude is far more than Tom reports. I have an application with notebook pages, each containing a form with labels and entries and a couple of buttons. Some have a treeview at the bottom, some do not. When I simply click the notebook tab of another page, it can take as long as 30 seconds for the screen to change. Under previous versions of Ubuntu, this was not an issue.

---

