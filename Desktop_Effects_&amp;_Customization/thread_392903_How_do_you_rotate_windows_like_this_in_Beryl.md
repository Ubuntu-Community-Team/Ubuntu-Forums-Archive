---
title: "How do you rotate windows like this in Beryl?"
date: 2007-03-25
forum: Desktop Effects &amp; Customization
---

### Post by herbster on 2007-03-25
[http://youtube.com/watch?v=NoF8_Ivdq1c](http://youtube.com/watch?v=NoF8_Ivdq1c)

At about 1:17 into the video, you can see a window being rotated horizontally.. how is this achieved??

(And for anyone who notices xwinwrap, it's available through Synaptic and you can check [http://swik.net/xwinwrap](http://swik.net/xwinwrap) to get it going, I did and it's mighty neat for a few seconds.)

---

### Post by Waappu on 2007-03-25
Hi

Do you mean window grouper pugin?
[http://wiki.beryl-project.org/wiki/Window_Grouper](http://wiki.beryl-project.org/wiki/Window_Grouper)

---

### Post by herbster on 2007-03-25
Waappu, thanks that worked perfectly! And I had it all this time, what an awesome feature!

---

### Post by rainwalker on 2007-03-25
What is the "super" key?

---

### Post by Waappu on 2007-03-25
> **rainwalker said:**
> What is the "super" key?

Hi

Windows key / Key with microsoft windows logo

Edit:
[http://wiki.beryl-project.org/wiki/Super_Key](http://wiki.beryl-project.org/wiki/Super_Key)

---

### Post by rainwalker on 2007-03-25
That's what I thought, and it's what I've been pressing, but nothing ever happens.

---

### Post by Waappu on 2007-03-25
Hi

Do you try to use Window Grouper ?
Have you enabled it in Beryl Setting Manager?

---

### Post by rainwalker on 2007-03-25
Oh...I don't think so, just a sec

---

### Post by rainwalker on 2007-03-25
Where do I enable it? I can't find it anywhere

---

### Post by Waappu on 2007-03-25
> **rainwalker said:**
> Where do I enable it? I can't find it anywhere

I have SVN version and that plug in can be found in Beryl Setting Manager-> Window Management.
It might be called Group and Tab Windows

---

### Post by rainwalker on 2007-03-25
Which section is it under? App. Window Switcher, Move Window, Place Windows, Put, Resize Window, Scale, Set Window Attribs, or Snapping Windows?

And what's an SVN version?

---

### Post by Waappu on 2007-03-25
> **rainwalker said:**
> Which section is it under? App. Window Switcher, Move Window, Place Windows, Put, Resize Window, Scale, Set Window Attribs, or Snapping Windows?

And what's an SVN version?

Hi

Group and Tab Windows is own plug in just as those you mentioned.

Try to update your Beryl. That plugin should be in latest version according this info.
[http://blog.beryl-project.org/?p=29](http://blog.beryl-project.org/?p=29)

SVN (currently GIT) is experimental and unsupported version.

---

### Post by herbster on 2007-03-25
rainwalker,

Open up a terminal and type:

```
beryl --version
```

Paste what it says, so we're sure which version you're using.

You should click on the top row of options called "Window Management," then the option you're looking for is Group and Tab Windows, it's second from the top for me.

Click the Shortcuts tab in this option and check to see what your shortcuts are for selecting and grouping windows. Basically, what you're doing is selecting multiple windows and grouping them, and then you can "Tab" them, which allows you to rotate multiple windows in just one.

My keys are set as Winkey+S = selects a window, Winkey+G = groups selected windows and then Winkey+left/right rotates.

Hope that helps!

---

### Post by rainwalker on 2007-03-25
It gives me "beryl-core 0.2.0"
I have no Group and Tab Windows, it's not there

---

### Post by Waappu on 2007-03-25
> **rainwalker said:**
> It gives me "beryl-core 0.2.0"
I have no Group and Tab Windows, it's not there

Hi

I don't know why you don't have that plugin :(
What repo you used to insrtall Beryl ?

---

### Post by rainwalker on 2007-03-25
I used the guide at [https://help.ubuntu.com/community/BerylOnEdgy](https://help.ubuntu.com/community/BerylOnEdgy)

---

### Post by Waappu on 2007-03-25
Hi

I don't know what is wrong

You can try this to install extra plugin package.
But better not try to fix something that is working....

Type in terminal```
killall beryl
killall beryl-manager
killall emerald
sudo aptitude install beryl-plugins-unsupported
```

and then restart beryl-manager

---

### Post by obbe on 2007-03-31
Hi everyone, I've the same problem..though I'm using beryl 0.2.0 i can't find this plugin..(I don't use the svn version) any ideas for add this plugin on my beryl? tnx

---

### Post by herbster on 2007-03-31
> **obbe said:**
> Hi everyone, I've the same problem..though I'm using beryl 0.2.0 i can't find this plugin..(I don't use the svn version) any ideas for add this plugin on my beryl? tnx

obbe,

I have only used the svn version of Beryl so far, and it has consistently worked great for me. The current svn version is up to 0.3.0 or so. You may want to consider uninstalling Beryl and installing the svn instead? Choice is yours of course.

---

### Post by obbe on 2007-03-31
ok i will try to install the svn version, but now i don't know how to unistall beryl  :confused:

---

### Post by sixfoottallrabbit on 2007-03-31
Open your terminal and run "sudo synaptic".

Search for "beryl", and with all of the items highlighted with a green box, right click them and there should be an option to change version. Change it to the latest SVN version, on all of the packages.

---

### Post by obbe on 2007-04-01
ok, i've installed the svn and work fine :)

---

