---
title: "Making Fluxbox Look Cool"
date: 2009-03-19
forum: Desktop Environments
---

### Post by orc_dragoon on 2009-03-19
Please give me some tips on how to make fluxbox look cool.

How do I get the app Bar thing?

So all tips are welcome.

---

### Post by kerry_s on 2009-03-19
> How do I get the app Bar thing?

what app bar thing?
you got to be more detailed/specific about what you want.
fluxbox has a basic toolbar, it doesn't do much but it works.
you can install others, google is the best way to find what you want.
for example to see what others have done:
[http://images.google.com/images?gbv=2&hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&q=fluxbox+&btnG=Search+Images](http://images.google.com/images?gbv=2&hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&q=fluxbox+&btnG=Search+Images)

---

### Post by ufuxlinux on 2009-03-19
I suggest you read Fluxbox wiki manuals as well as Gentoo Fluxbox documents. You can use idesk package for desktop icons and rox for a lightweight file manager. If you want some lightweight information on your desktop, you can use conky as well. Google for these, you can find informations about configuration files.

---

### Post by orc_dragoon on 2009-03-19
> **kerry_s said:**
> what app bar thing?
you got to be more detailed/specific about what you want.
fluxbox has a basic toolbar, it doesn't do much but it works.
you can install others, google is the best way to find what you want.
for example to see what others have done:
[http://images.google.com/images?gbv=2&hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&q=fluxbox+&btnG=Search+Images](http://images.google.com/images?gbv=2&hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&q=fluxbox+&btnG=Search+Images)

Its something to do with gdesklets or something like that.

---

### Post by kerry_s on 2009-03-19
> **orc_dragoon said:**
> Its something to do with gdesklets or something like that.

if you can find a pic and point us to it, we most likely can tell you what it is. linux has lots of programs, guessing without seeing can take a long time. also keep in mind programs come and go it might no longer be available or does not work with your wm. it's also up to the user, there's a lot of smart people out there that can do some amazing things with a gui.

for example i use jwm, looks like this=> [http://joewing.net/programs/jwm/screenshots/jwm-2.0.png](http://joewing.net/programs/jwm/screenshots/jwm-2.0.png)

mine looks like this=>

---

### Post by orc_dragoon on 2009-03-19
Im looking for something like this

[http://media.photobucket.com/image/gdesklets%2B%252B%2Bfluxbox/capheind/Screenshotsept.png](http://media.photobucket.com/image/gdesklets%2B%252B%2Bfluxbox/capheind/Screenshotsept.png)

Also how do I get idesk to start on startup.

---

### Post by kerry_s on 2009-03-19
that launcher is wbar> sudo apt-get install wbar
[http://www.linux.com/feature/128982](http://www.linux.com/feature/128982)

put:

idesk &

into your ~/.fluxbox/startup

post the startup if your not sure where to put it and i'll add it so you can copy.

you might also want to check out adesklets, should be in the repo.
[http://adesklets.sourceforge.net/screenshots.html](http://adesklets.sourceforge.net/screenshots.html)

---

### Post by Tacuabe on 2009-05-09
Here's my contribution to this issue. I use Ubuntu 8.10, Fluxbox and Rox filer. Styling Fluxbox is quite easy and there are plenty of tutorials out there. Anyhoo, take a look at the enclosed style file (theme.cfg) to see one way of doing it. 

I enclose all the files you need to reproduce my layout. The dock is actually a Rox panel, small, fast, easy to configure and located at any of the four edges of the screen.

In files.zip there is a shutdown-reboot text file. This line should be included in /etc/sudoers file to allow for passwordless shutdown and rebooting. Must be root to do that. Make a backup copy of sudoers just in case.

For the style, put theme.cfg in /home/yourname/.fluxbox/styles and the pixmaps in .../styles/pixmaps. Theme.cfg is the file that defines all aspects of the style itself. Worth reading if you plan to modify it or create a new one.

Install the fonts as usual, this makes them accessible to the style.

Do write to me if you need any help. Good luck!

---

### Post by haiyun211 on 2009-05-28
Hi all.  Does any one know how to make the terminal transparent?

---

### Post by Anzan on 2009-05-30
You can make gnome-terminal transparent in Profile Preferences.

---

### Post by stanca on 2009-08-23
Here's mine:;)
wbar
conky
gkrellm(with gkrellfire plugin)
xcompmgr
transset-df
3ddesktop
slit
etc...

---

