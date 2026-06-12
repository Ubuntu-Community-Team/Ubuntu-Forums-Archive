---
title: "Java Applets in Firefox won't regain keyboard focus"
date: 2009-02-25
forum: General Help
---

### Post by sigmazero13 on 2009-02-25
I've been playing around with a few Java Applets in Firefox 3.0.6 on Ubuntu 8.10, and have come across something very frustrating.  Usually, as soon as the page loads, the applet will receive keyboard input just fine.  However, if the applet ever loses keyboard focus (be it by going to another tab, window, or even just clicking elsewhere on the same page), it seems to be impossible to get the keyboard focus back.

The strange thing is that the applet is still able to receive mouse events after losing keyboard focus; ie, I can click on the applet, and a mousepressed event is triggered.  I wrote a dummy applet on my computer to test this, and found that calling the "requestFocusInWindow()" method always gets "false", meaning it was guaranteed NOT to get focus for whatever reason.

This seems to be a bug with either Firefox for Ubuntu or the OS itself; when I run the applet using appletviewer, it behaves just fine.  I'm thinking it may be the browser, like the browser refuses to return focus to the browser. 

I've tried uninstalling and reinstalling both firefox, java, and the java plugin for firefox, and none of that helped.  

Thanks in advance!

---

### Post by nonporous on 2011-06-23
I've noticed the same exact issue (Ubuntu 10.04 LTS), and I'd like to bump this old thread. It's very frustrating.

---

### Post by johnkaplantech on 2011-08-17
Note this isn't a Ubuntu- or Firefox-only problem. It happens on Mac OSX (I have 10.6.7) on both Firefox and Safari. I haven't seen it on Windows with either Firefox or IE, but that likely doesn't make you feel any better.  

Javascript can play with the keyboard focus and it doesn't automatically go back to the applet the way it should when you click, so in my app it seems to behave randomly depending on where you happen to click first. The strange part is that mouse events are handled just fine & focus is never a problem there.

I saw some javascript snippets that try to force the focus back to the applet, along the lines of:
    if(!document.AppletName.isActive())
      document.AppletName.requestFocus();

I'm going to experiment & see if I can get something like this to work.
Hope that helps.
- John

---

### Post by drdanielfc on 2011-09-25
Have any of you found a solution? I have the same problem and it is making it quite difficult to develop an applet when I can't even promise the user will have the ability to gain focus....

---

### Post by Dabo Ross on 2012-12-28
I am experiencing the same problem, But I have noticed that a few applets can still get keyboard input by key binding.

I believe this could solve the problem for developers.

I am currently researching it, and I found this page on key binding: [http://docs.oracle.com/javase/tutorial/uiswing/misc/keybinding.html](http://docs.oracle.com/javase/tutorial/uiswing/misc/keybinding.html)

---

### Post by overdrank on 2012-12-28
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

