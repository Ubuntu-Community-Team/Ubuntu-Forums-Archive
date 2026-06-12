---
title: "Getting Cool Screensavers"
date: 2011-03-16
forum: Desktop Environments
---

### Post by WlaadDyaab on 2011-03-16
Getting Cool Screensavers

(I'm using the Seamonkey Internet Browser for my own reasons. If you want to download it: Applications > Ubuntu Software Centre. Now we're in "Ubuntu Software Centre" box: Internet > Web Browsers > Seamonkey Navigator . Install. To see and use it: Applications > Internet > Seamonkey)

Linux distro: Ubuntu 10.10
Internet Browser: Seamonkey

I got the idea from this YouTube link: [http://www.youtube.com/watch?v=nEQtAU7NdfU&feature=channel_video_title](http://www.youtube.com/watch?v=nEQtAU7NdfU&feature=channel_video_title)

Step-by-step:

- [http://reallyslick.com/](http://reallyslick.com/)
- Downloads
- Tugrul Galatali

- [http://rss-glx.sourceforge.net/](http://rss-glx.sourceforge.net/)
- Under "Download:", "Source":
  Just after it says "tar/bzip2:". Click on "All in one"

- On my Internet Browser Seamonkey, a box will pop-up "Opening rss-glx_0.9.1.tar.bz2"
- Tick the "Save File" option
- "OK"
- It's going to be saved to your "Downloads" repository folder. Click on "Save"

- Places > Downloads
- Right-click "rss-glx_0.9.1.tar.bz2" > Extract Here
- You will see that you have a normal folder now called "rss-glx_0.9.1". You don't have to do nothing to it

- Applications > Ubuntu Software Centre
- In "Ubuntu Software Centre" box, copy/paste in the search bar "xscreensaver"

- Click on "ReallySlick Screensavers GLXPort" > Install
- Type your password > Authenticate

- System > Preferences > Screensaver
- On "Screensaver Preferences" you'll see a variety of Screensavers, I think they'll be 27 Screesavers all together :)

Still want more?

- Applications > Ubuntu Software Centre
- In "Ubuntu Software Centre" copy/paste "xscreensaver" in the search bar
- Click on "GL (Mesa) screen hacks for xscreensaver" > Install
- Type your password > Authenticate

- System > Preferences > Screensaver
- In the "Screensaver Preferences" box you'll see that there's a little bit more Screensavers (probably around 35 altogether now)

Still want more?

There's a lot more as you Install the other files from the "Ubuntu Software Centre" box under "xscreensaver" results

As for me, I'm only interested in this simple screensaver called "Hufo's Smoke" so I'll stick to that and I hope you found these instructions simple and basic to understand

Don't forget that you don't have to install too much stuff that your computer system can't take. Your choice at the end of the day

As for the Internet Browser I'm using (Seamonkey), I personally prefer Firefox over all the Internet Browsers but I've been getting in certain issues with the wireless card since the start of installing Ubuntu on my Laptop...etc

Any Internet Browser is fine. I specified what Internet Browser I'm using because I've got some Flash Player issues, where YouTube doesn't work on Chromium, so I've got Seamonkey as a conclusion

Any suggestions, please do post it (I'm allways learning). Any problems - glad to help :)

Good luck :)

---

### Post by wojox on 2011-03-16
I like Sonar. I make it ping all my boxes I ssh into. :P

---

### Post by WlaadDyaab on 2011-03-16
> **wojox said:**
> I like Sonar. I make it ping all my boxes I ssh into. :P

How to you get Sonar? And what's "ping"?

"ssh" Is that a command in Terminal?

Sorry I'm confused Lol

---

### Post by wojox on 2011-03-16
> **WlaadDyaab said:**
> How to you get Sonar? And what's "ping"?

"ssh" Is that a command in Terminal?

Sorry I'm confused Lol

Ya Sonar should be in there or xscreensaver-gl-extra. Open your terminal and run **screensaver-manager**

It's a big sonar that spins and pings your hosts in your ~/.ssh directory.

---

### Post by WlaadDyaab on 2011-03-16
> **wojox said:**
> Ya Sonar should be in there or xscreensaver-gl-extra. Open your terminal and run **screensaver-manager**

It's a big sonar that spins and pings your hosts in your ~/.ssh directory.

I seen it now on Google images: [http://www.google.co.uk/imgres?imgurl=http://www.jwz.org/xscreensaver/screenshots/sonar.jpg&imgrefurl=http://www.jwz.org/blog/2008/12/xscreensaver-508/&usg=__tiSlFgbBrhIfhO1aNCCjYHtnefc=&h=150&w=200&sz=30&hl=en&start=1&zoom=1&um=1&itbs=1&tbnid=qPEfM7xqLI4mJM:&tbnh=78&tbnw=104&prev=/images%3Fq%3Dsonar%2Bscreensaver%2Bubuntu%26um%3D1%26hl%3Den%26sa%3DN%26tbs%3Disch:1&ei=FkmBTcCAK4uYhQeRncmwBA](http://www.google.co.uk/imgres?imgurl=http://www.jwz.org/xscreensaver/screenshots/sonar.jpg&imgrefurl=http://www.jwz.org/blog/2008/12/xscreensaver-508/&usg=__tiSlFgbBrhIfhO1aNCCjYHtnefc=&h=150&w=200&sz=30&hl=en&start=1&zoom=1&um=1&itbs=1&tbnid=qPEfM7xqLI4mJM:&tbnh=78&tbnw=104&prev=/images%3Fq%3Dsonar%2Bscreensaver%2Bubuntu%26um%3D1%26hl%3Den%26sa%3DN%26tbs%3Disch:1&ei=FkmBTcCAK4uYhQeRncmwBA)

Sorry wojox I'm still not getting anything on Terminal

I done this:

Copy/paste "xscreensaver-gl-extra" into Terminal but no luck. I get Terminal saying this > xscreensaver-gl-extra: command not found


---

### Post by wojox on 2011-03-16
No try:

```
sudo apt-get install xscreensaver-gl-extra
```

---

### Post by tgalati4 on 2011-03-16
I like webilder gnome applet.  It grabs backgrounds from various places.  I have mine changed every 30 minutes.

sudo apt-get install webilder

---

### Post by WlaadDyaab on 2011-03-16
> **wojox said:**
> No try:

```
sudo apt-get install xscreensaver-gl-extra
```

Heey thanks for that!

At the start it never worked in Terminal:

I copy/paste what you told me to do > sudo apt-get install xscreensaver-gl-extra

But Terminal gave me this: > Reading package lists... Done
Building dependency tree       
Reading state information... Done
xscreensaver-gl-extra is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


So I just typed this in the "Ubuntu Software Centre" search bar- Applications > Ubuntu Software Centre: xscreensaver sonar

Then I installed "data files to be shared among screensaver frontends"

Then:

System > Preferences > Screensaver

And there it was: 

- Screensaver Preferences
- Screensaver theme: Sonar

Yea that was also a cool Screensaver :)

---

### Post by WlaadDyaab on 2011-03-16
> **tgalati4 said:**
> I like webilder gnome applet.  It grabs backgrounds from various places.  I have mine changed every 30 minutes.

sudo apt-get install webilder

Heey thanks a lot for the information tgalati4

I've just seen this YouTube link talking about this cool feature :)

[http://www.youtube.com/watch?v=Bo7c__Jsp0o](http://www.youtube.com/watch?v=Bo7c__Jsp0o)

---

