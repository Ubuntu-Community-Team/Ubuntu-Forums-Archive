---
title: "gedit takes forever to open a simple, light, text document on Intrepid"
date: 2008-11-02
forum: Desktop Environments
---

### Post by jokker on 2008-11-02
Everything is in the title... Used to be very fast on previous ubuntu releases, but since intrepid gedit takes a very very long time to open a document (plain text, few characters, few bytes)
launched through terminal, no errors. Go figure ! :confused:

---

### Post by tuxxy on 2008-11-02
Hey this is a bug im sure as had the same issue but most of the time it would simply crash gedit, I filed a bug report for this but occasionally it worked for me even if rather slow, this was an upgrade to Ibex so had a feeling it would be ok with a fresh install so I removed the bug report.

Now you have the same issues so heres the [new bug report]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/292853") please post a comment stating your problem is the same and system details, thanks!

[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/292853](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/292853)

---

### Post by NilsE on 2008-11-02
While waiting for the bug fix in the meantime you can go into 

Edit >Preferences > Plugins 

and turn off the File Browser pane.

---

### Post by tuxxy on 2008-11-02
> **NilsE said:**
> While waiting for the bug fix in the meantime you can go into 

Edit >Preferences > Plugins 

and turn off the File Browser pane.

thankyou NiLsE thats sorted mine, ill add it to the report and get it closed :)

---

### Post by NilsE on 2008-11-02
> **tuxxy said:**
> thankyou NiLsE thats sorted mine, ill add it to the report and get it closed :)
Glad it worked for you.  There are a few dups of this bug and I know I added this to one of them.

---

### Post by jokker on 2008-11-02
Worked for me too... thanks

---

### Post by ferchon03 on 2008-11-03
> **NilsE said:**
> While waiting for the bug fix in the meantime you can go into 

Edit >Preferences > Plugins 

and turn off the File Browser pane.

Thank You!, works great.

---

### Post by mshipman on 2008-11-03
Gedit has been driving me mad since I upgraded. This was very helpful!

---

### Post by Spike-X on 2008-11-06
> **NilsE said:**
> While waiting for the bug fix in the meantime you can go into 

Edit >Preferences > Plugins 

and turn off the File Browser pane.
This worked for me too, thanks!

---

### Post by rudihawk on 2008-11-06
> **NilsE said:**
> While waiting for the bug fix in the meantime you can go into 

Edit >Preferences > Plugins 

and turn off the File Browser pane.

Thanks that fixedc it :)

---

### Post by Enmi on 2008-11-10
This thread shed a lot of light into this odd problem for me.

And if you're like me... wondering how to even GET to Gedit's menu, if it keeps hanging after it shows up on screen, you'll want to know there's another way to disable the file browser plugin.

If you've already installed it, open the Configuration Editor (use Synaptic to add it, if you haven't) 

Browse to: /apps/gedit-2/plugins/

From there, just double click on "active-plugins" and find the line listing filebrowser and click remove. After that, Gedit should load fine.

I was kinda used to that plugin... I do hope that's fixed sometime soon. :(

---

### Post by robertyou on 2008-11-17
> **NilsE said:**
> While waiting for the bug fix in the meantime you can go into 

Edit >Preferences > Plugins 

and turn off the File Browser pane.

Sweet..thanks a lot!

---

### Post by xcesarfrancox on 2008-11-18
> **NilsE said:**
> While waiting for the bug fix in the meantime you can go into 

Edit >Preferences > Plugins 

and turn off the File Browser pane.

Thank you! it worked for me, but I read it had something to do with the icon theme (while using human and File Browser Pane enabled gedit opened flawlessly, but the I changed the icon theme to another and gedit got slow again... so I disabled the File Browser Pane)

---

### Post by DiscoSuperstar00 on 2008-11-20
This fixed it for me too, but I agree with the above poster, this problem appeared when I switched to a new icon theme and seems caused by that. An strace showed many calls to load the icon files that each took a really long time.

---

### Post by neotasic1 on 2008-11-22
> **NilsE said:**
> While waiting for the bug fix in the meantime you can go into 

Edit >Preferences > Plugins 

and turn off the File Browser pane.

Thanks NilsE - worked a charm. Thanks also to Enmi for info on how to do it if text editor doesn't load properly. (didn't actually hang, just took an eternity to load)

---

### Post by ameseisch on 2008-11-27
I am really hoping this issue is fixed soon. turning off the file browser pane isn't really a good solution for me. Luckily my filebrowser is just really slow. it doesn't crash gedit. I agree that the icon issue might be the culprit.

---

### Post by [ITA]ArgH on 2008-12-01
thanks worked for me!!
I really appreciate this forum :guitar:

---

### Post by elgalloloco on 2009-01-19
> **NilsE said:**
> While waiting for the bug fix in the meantime you can go into 

Edit >Preferences > Plugins 

and turn off the File Browser pane.

Thanx...

I was having the same problem on openSUSE 11.1, and this worked perfectly!

---

### Post by adamlau on 2009-01-19
You guys could also give Mousepad a try. Not MDI and no plugin support, but fast and stable.

---

### Post by gramound on 2009-06-29
I thought I had the same symptoms this morning after I updated my Ubuntu (Jaunty).
I had performance problems, disabled the gedit filebrowser plugin, and things got much faster.

I jumped to the conclusion that I was victim of a "relapse" of an earlier bug patched in November 2008:
[http://bugzilla.gnome.org/show_bug.cgi?id=554362]("http://bugzilla.gnome.org/show_bug.cgi?id=554362")

However I realized the performance is affected by something else, because all applications are affected. The filebrowser plugin is simply making it worse...

---

