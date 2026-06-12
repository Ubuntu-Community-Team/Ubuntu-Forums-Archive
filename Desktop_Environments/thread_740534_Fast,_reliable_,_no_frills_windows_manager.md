---
title: "Fast, reliable , no frills windows manager ?"
date: 2008-03-30
forum: Desktop Environments
---

### Post by Biased turkey on 2008-03-30
Is there any "windows manager shootout" thread ?
I used the search engine but didn't get any result.
Could Blackbox fit the bill ?
Tia for any suggestion

Jacques

---

### Post by Masteroc on 2008-03-30
Your main options for "no frills" would be (imho): Openbox, Blackbox, IceWM and Fluxbox. Googling turns up some good discussions, also check out this link to how to set up low memory systems from the ubuntu wiki: [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by urukrama on 2008-03-31
I would go for Openbox. It is a simple ('no frills') but powerful window manager. It is light and fast, and can be very aesthetically pleasing. There are quite a number of Openbox users here (and elsewhere), so if you run into problems you'll receive some support. Have a look at the guide linked to in my signature for help setting up Openbox.

Blackbox resembles Openbox, but is no longer developped and (compared to Openbox) lacks in features.

Icewm is a good candidate if you like a typical Windows 98 layout. There are some good themes available (see box-look.org), it is light, simple to configure and there are enough users here to help you out if needed.

As for threads about window managers on these forums: [here]("http://ubuntuforums.org/showthread.php?t=734424") and [here]("http://ubuntuforums.org/showthread.php?t=299424") are a few recent ones.

---

### Post by kpkeerthi on 2008-03-31
I recommend Openbox. I use it with Arch.

---

### Post by Biased turkey on 2008-03-31
First, thanks to the Ubuntu forum members who took some of their precious time to reply.
I  checked Enlightenment, blackbox and openbox websites.
Your suggestions are unanimous to recommend Openbox.
I installed Openbox and I'm very pleased with it. As advertised , it is fast and simple ,some would even say "spartan" :) . And it looks good too.
Special thank s to urukrama for the various links and for the complete Openbox guide

Jacques

---

### Post by urukrama on 2008-03-31
> **Biased turkey said:**
> Special thank s to urukrama for the various links and for the complete Openbox guide


You're welcome. I'm sure you'll love Openbox even more when you've been using it for a while. It is a great window manager and the developers are going into a great direction.

---

### Post by kerry_s on 2008-03-31
jwm is fantastic.

stock-> [http://joewing.net/programs/jwm/screenshots/jwm-2.0.png](http://joewing.net/programs/jwm/screenshots/jwm-2.0.png)

mines really tweaked.

---

### Post by Biased turkey on 2008-03-31
Just to compare Openbox with a yardstick, I installed IceWM.
I think both are fine windows managers.
Just my opinion here but any  minimalistic windows manager should at least include  a file browser and a taskbar..
I know Openbox and IceWM can have both add-on to do what I'm looking for.
 The beauty of Linux : free as in free beer . I know what it means because  I'm a homebrewer  :)

Jacques

---

### Post by scottro on 2008-03-31
Fluxbox has a taskbar (but no builtin file browser).  :)

I'm surprised no one mentioned it--I wonder if it's become so popular, it's no longer geeky. 

I prefer it over openbox for a few reasons--note these are my personal tastes. 
One, the toolbar is there. 
Two, it has a thing where you can have a particular thing remember its position for next time (this is useful for me with one particular application, an old mailbox watcher, xbuffy.  I'm sure there's a way to do it in openbox as well, I simply haven't gotten around to finding it.
Most important, the simplicity of its config files.  For example to have the Windows key and j move a window down 50 pixels (j is used because I'm used to vi, and j is the vi keystroke to move down)

Mod4 j :MoveDown 50

In openbox
<keybind key="W-j">
    <action name="MoveRelative">
<x>0</x>
<y>50</y>
</action>
  </keybind>

(I'm not sure if I could eliminate the <x>0</x> line, but even without it, it's quite a bit more to type.)

Many people find openbox snappier than fluxbox, but I haven't found that to be the case.  
If you want to go really minimalist, there's also weewm and evilwm.

---

### Post by eriqjaffe on 2008-04-01
> **Biased turkey said:**
> Just my opinion here but any  minimalistic windows manager should at least include  a file browser and a taskbar.At that point, they'd pretty much become desktop environments.  I like the fact that I can choose which file manager and taskpar/panel I want, personally.  The modularity of it all really suits me.

---

### Post by urukrama on 2008-04-01
> **Biased turkey said:**
> Just my opinion here but any  minimalistic windows manager should at least include  a file browser and a taskbar.

Perhaps [LXDE]("http://ubuntuforums.org/showthread.php?t=707008") is for you then. Check it out. It uses Openbox as a window manager.

---

### Post by Biased turkey on 2008-04-02
I downloaded and installed lxde, but could someone please tell me how to start lxde ? ( I don't see it in the windows manager list when I login )

Jacques

---

### Post by PCMan on 2008-04-02
> **Biased turkey said:**
> I downloaded and installed lxde, but could someone please tell me how to start lxde ? ( I don't see it in the windows manager list when I login )

Jacques

Please use this apt repo instead.
[http://ubuntuforums.org/showthread.php?t=738958&highlight=lxde](http://ubuntuforums.org/showthread.php?t=738958&highlight=lxde)

The article you previously read is already out-of-date.

---

### Post by Biased turkey on 2008-04-02
> **PCMan said:**
> Please use this apt repo instead.
[http://ubuntuforums.org/showthread.php?t=738958&highlight=lxde](http://ubuntuforums.org/showthread.php?t=738958&highlight=lxde)

The article you previously read is already out-of-date.

Thank you for the suggestion PCMan. I added the repository to the list in the package manager.
 After reloading I could see lxde in the available  packages list but when I try to install lxde I gives some dependency problem so I didn't insist and removed the repository from the list.

Jacques

---

