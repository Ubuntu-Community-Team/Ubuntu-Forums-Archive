---
title: "[SOLVED] GNOME, XFCE, and speed"
date: 2008-10-27
forum: Desktop Environments
---

### Post by fiddler616 on 2008-10-27
Hello,
I've been using GNOME for awhile, on a laptop with 512 MB RAM and 1000mhZ processor. I've tried out 
```
sudo aptitude install xubuntu-desktop
```
and really like XFCE too.
However, were I to permanently switch to XFCE, I'd still want:
[LIST]
[*]OpenOffice
[*]Nautilus
[*]Firefox (I think XFCE has it natively though)
[*]gedit
[*]gnome-terminal
[*]Dia
[*]kolourpaint
[/LIST]
And I understand that running GNOME apps on XFCE subtracts from the speed.
The question is:
Will  there be a noticeable increase in speed if I switch to GNOME-heave XFCE?
...also:
Is XFCE spelled XFCE or Xfce? (I've seen both)
Is there an easy way to change the color/transparency of the panes in Xfce?
Thanks in advance.
PS: I know this has been covered before, but it was an earlier version of Ubuntu/GNOME/Xfce.

---

### Post by OrangeCrate on 2008-10-27
I'm currently running Xfce/Intrepid, and have Xfce/Hardy on another partition. It was also the same with Feisty and Gutsy.

On both of my computers, Xfce always seems a bit quicker than Gnome (particularly on my older computer, a 1.4 GHz Celeron, with 512 meg of RAM), though my reason for installing, is that I simply prefer Xfce's interface.

And, I'm with you, I like to have the full range of default Ubuntu packages such as OOo, Xsane, etc, working "out of the box", so to speak.

If you go to a straight Xubuntu (Xfce) install, you can get everything you want, but you'll have to install OOo, as an example, from Synaptic, or the command line. I actually did that with Gutsy, and Xubuntu was certainly quick. No Nautilus though, you'll be using Thunar. (See additional comment in the next post.)

See here for additional installation instructions...

[http://psychocats.net/ubuntu/xubuntu](http://psychocats.net/ubuntu/xubuntu)

---

### Post by OrangeCrate on 2008-10-27
^^,

Sorry, forgot to comment on a couple of your other concerns...

First,

> Is there an easy way to change the color/transparency of the panes in Xfce?

Transparency yes, color no, not that I'm aware of. Go Menu > Settings > Settings Manager > Window Manager Tweaks > Compositor, and you can modify a lot of stuff.

Second,

Nautilus will be available from a Gnome session, but you'll be using Thunar on Xfce. All the same file structure though. (Tip - it's easier to install themes, icons, etc. from Gnome, than it is from Xfce. Install on Gnome, they'll show up on Xfce.)

IMO, installing Xfce over Ubuntu is the best way to go, since you're getting the best of both worlds, but either way should serve you well.

---

### Post by mali2297 on 2008-10-27
> **fiddler616 said:**
> 
Will  there be a noticeable increase in speed if I switch to GNOME-heave XFCE?

I found the most noticeable difference in speed when comparing the file managers. Consider giving Thunar another try.

> 
Is XFCE spelled XFCE or Xfce? (I've seen both)

From the [wiki](http://wiki.xfce.org/faq#about_xfce):
> 
How to pronounce Xfce and what it means

&#8220;Ecks Eff See Eee&#8221;. The name Xfce originally stood for XForms Common Environment, but since then, Xfce was rewritten twice and doesn't use XForms toolkit anymore. The name survived, but the F is nolonger capitalized (not &#8220;XFce&#8221;, but &#8220;Xfce&#8221;). Currently the acronym doesn't stand for anything (suggestion: X Freakin' Cool Environment).


> 
Is there an easy way to change the color/transparency of the panes in Xfce?

You can change transparency if you right-click on the panel and go to Customize Panel. The color is controlled by the gtk+ theme; I don't know an 'easy' way of editing it, but it is possible to craft it manually. Perhaps it is easiest to search for a suitable theme at [www.xfce-look.org](www.xfce-look.org).

---

### Post by OrangeCrate on 2008-10-27
> **mali2297 said:**
> I found the most noticeable difference in speed when comparing the file managers. Consider giving Thunar another try.


From the [wiki](http://wiki.xfce.org/faq#about_xfce):



**You can change transparency if you right-click on the panel and go to Customize Panel. **The color is controlled by the gtk+ theme; I don't know an 'easy' way of editing it, but it is possible to craft it manually. Perhaps it is easiest to search for a suitable theme at [www.xfce-look.org](www.xfce-look.org).

Right, assuming you've checked "Enable display compositing" in the "Compositor" section of the "Window Manager Tweaks". If that box is unchecked, there is no option to control transparency under "Customize Panel".

I'm only pointing this out, to head off the inevitable question of not seeing the option when you right click the panel, and follow your instructions. At least that's the way it has to be on both of my computers.

---

### Post by sub2007 on 2008-10-27
To be honest, Xubuntu actually has a lot of GNOME libraries and programs installed out of the box. You might well be able to run those apps just with the libs you get out of the box or with only installing a few more. I don't think you'll find an awful lot of speed change by installing those apps you listed (except for kolourpaint which will also need KDE libs installed).

---

### Post by fiddler616 on 2008-11-02
Wow, thank you guys. I'd go out and try it right now, except I'm currently posting from a Live CD--GRUB has a few "boo-boo's."
I'll definitely get back about using Thunar, etc.
Is it possible to *just* install the Xfce Desktop Environment, and not all the additional packages that come with xubuntu-desktop? Because when I've done it before, I get a lot of Xfce stuff that I don't really want--since I use the GNOME equivalent.
In the same line of reasoning, is it possible to just remove GNOME--and keep the packages (i. e.: OO.o, Firefox, etc.) that come with it?
Thanks.

---

### Post by mali2297 on 2008-11-02
> **fiddler616 said:**
> 
Is it possible to *just* install the Xfce Desktop Environment, and not all the additional packages that come with xubuntu-desktop?

Yes, install the meta package [xfce4]("http://packages.ubuntu.com/intrepid/xfce4").

---

### Post by fiddler616 on 2008-11-02
> **mali2297 said:**
> Yes, install the meta package [xfce4]("http://packages.ubuntu.com/intrepid/xfce4").

Aha! Thanks.

(Now if I can just get off this Live CD....)

---

### Post by Warren Watts on 2008-11-02
> **fiddler616 said:**
> 
Is it possible to *just* install the Xfce Desktop Environment, and not all the additional packages that come with xubuntu-desktop? 

I wrote a HOWTO (HOWTO Build and install a compact (+/-) 1GB Xfce Based Ubuntu Desktop) you might find useful as well...

[http://ubuntuforums.org/showthread.php?t=549958](http://ubuntuforums.org/showthread.php?t=549958)



.

---

### Post by fiddler616 on 2008-11-04
A) I got my computer working
B) I installed the xfce4 package, and Thunar.
I logged into Xfce...[str]and where's my panel? There's this square monstrosity on my desktop, and upon right-clicking it I learned that *it* is my new panel.[/str]
...
I started this post to rant about how much I hated the new panel (it definitely didn't look like that when I played with Xfce in Hardy,) but then I realized it was a lot more customizable than I was giving it credit for. I think I used Windows a little bit too much today (but, but I got to use Chrome for the first time, and it's so cool! :) )
At any rate, what's up with the workspaces? I'm only allowed to adjust the rows? No columns? What?

As for customizing panel color/transparency, opening up the "Customize Panel" box doesn't help.

[str]Just out of curiosity, what does the little radio-button thing in the panes of all my windows do?[/str] Edit: Figured it out

Thanks for all your help.

---

### Post by the Arbiter on 2008-11-04
hi im the arbiter and i wuz wundering if anywon could tell me if there is a windows blackcomb theme for gtk2.x like Style xp's watercolor theme....


xubuntu8.10 4gb hdd 354mb ram intel pentium 3 450Mhz

---

### Post by fiddler616 on 2008-11-05
> **the Arbiter said:**
> hi im the arbiter and i wuz wundering if anywon could tell me if there is a windows blackcomb theme for gtk2.x like Style xp's watercolor theme....


xubuntu8.10 4gb hdd 354mb ram intel pentium 3 450Mhz

Hmm, I'm sorry I can't explicitly help you. But you'll probably do much better if  you start a new thread.

---

### Post by mali2297 on 2008-11-05
> 
At any rate, what's up with the workspaces? I'm only allowed to adjust the rows? No columns? What?

You can set the total number of workspaces through *Settings Manager -> Workspaces and Margins* and thus indirectly set the number of columns.

> 
As for customizing panel color/transparency, opening up the "Customize Panel" box doesn't help.

Did you enable compositing through *Settings Manager -> Window Manager Tweaks* as OrangeCrate suggested?

---

### Post by fiddler616 on 2008-11-05
> **mali2297 said:**
> You can set the total number of workspaces through *Settings Manager -> Workspaces and Margins* and thus indirectly set the number of columns.

Thanks.
> 
Did you enable compositing through *Settings Manager -> Window Manager Tweaks* as OrangeCrate suggested?
Sorry, when I was re-reading (er, skimming) this thread from Xfce I missed it.

Solved!

---

