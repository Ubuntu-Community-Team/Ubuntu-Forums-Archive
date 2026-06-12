---
title: "Replace switcher icon in Gnome shell"
date: 2012-02-27
forum: Desktop Environments
---

### Post by cortman on 2012-02-27
I'm working on editing a Gnome shell theme to my liking. The current theme currently just has the word "Activities" in the top left corner for the app switcher. I'd like to change that to an image of my choosing, but if I try and drag-drop an image "paragraph" from another CSS sheet into it, the shell crashes. And I'm not sure where it gets the info to call it "Activities".
Anyone know how to get this working?

---

### Post by MARP1961 on 2012-02-28
There is an extension that might be able to do what you want:
[https://extensions.gnome.org/extension/77/activities-button-text/](https://extensions.gnome.org/extension/77/activities-button-text/)
I haven't tried it yet!

---

### Post by cortman on 2012-02-28
Thanks, but that's not going to work. I'm wanting to know how to edit the CSS stylesheet to change the icon/text/etc. in the corner.

---

### Post by MARP1961 on 2012-02-28
Hello again Cortman. You clearly know much more than me about making these kind of alterations but is this of interest to you?

[http://blog.fpmurphy.com/2011/04/replace-gnome-shell-activities-text-string-with-icon.html](http://blog.fpmurphy.com/2011/04/replace-gnome-shell-activities-text-string-with-icon.html)

Please forgive me if I have misunderstood what you are trying to do. Hopefully someone else will be able to advise.

---

### Post by cortman on 2012-02-28
> **MARP1961 said:**
> Hello again Cortman. You clearly know much more than me about making these kind of alterations but is this of interest to you?

[http://blog.fpmurphy.com/2011/04/replace-gnome-shell-activities-text-string-with-icon.html](http://blog.fpmurphy.com/2011/04/replace-gnome-shell-activities-text-string-with-icon.html)

Please forgive me if I have misunderstood what you are trying to do. Hopefully someone else will be able to advise.

THAT looks like what I'm looking for! Thanks very much, I can't believe I didn't think to check FP Murphy's blog. So much for a keen sense of the obvious...
Thanks very much!

---

### Post by cortman on 2012-02-28
OK, I'm bumping this back up again. After a more careful perusal of the site, I realize it wants to either

a) edit the /usr/share/blah/blah/blah.json file, which as Finn points out will get overwritten every time you update or reload the theme,

b) or create a shell extension in ~/local/share/gnome-shell/blah/blah. I want to do neither; I want the theme to be portable to different computers (and downloadable) as a single .zip file.

So any ideas?

---

### Post by cbowman57 on 2012-02-28
The existing theme that incorporated an Activities icon (& maybe text) is/was Pantheon.

I prefer using the applications menu extension that replaces the shell default myself but by dissecting Pantheon there might be something to help you figure it out.

---

