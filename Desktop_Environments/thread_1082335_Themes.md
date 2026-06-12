---
title: "Themes??"
date: 2009-02-27
forum: Desktop Environments
---

### Post by burdock on 2009-02-27
Hey all,

Working on getting ubuntu set up on my laptop. Its going well so far but I have run into a bit of trouble when trying to change the desktop around.

I'd like it to use a theme (or whatever this is)..
[http://gnome-look.org/content/show.php/BlueSpace?content=73599](http://gnome-look.org/content/show.php/BlueSpace?content=73599)

Spefically, Id like to have the "launcher" bar that is on the bottom of the screenshot.

But I cant figure out how to make it work. I believe I have installed gnomenu correctly, although Im not entirely sure I even need it...

Can someone point me in the right direction?

Thanks
Cole

---

### Post by oldos2er on 2009-02-27
That's AWN, Avant window navigator. It's in the repositories.

---

### Post by hictio on 2009-02-27
> **burdock said:**
> 
Spefically, Id like to have the "launcher" bar that is on the bottom of the screenshot.


What version of Ubuntu are you running?
If you are on Intrepid, all you have to do to install it on your box is:

```

aptitude install avant-window-navigator ENTER

```


That is, type that (or copy paste) onto a Terminal (Applications > Accessories > Terminal) from an Ubuntu Intrepid box connected to the internet.

---

### Post by ad_267 on 2009-02-27
You'd need a "sudo" in front of that command to get root user privileges:
```
sudo aptitude install avant-window-navigator
```
Then you'll have to enter your password.

You can also achieve the same thing by installing avant-window-navigator from System - Administration - Synaptic Package Manager.

---

### Post by hictio on 2009-02-27
> **ad_267 said:**
> You'd need a "sudo" in front of that command to get root user privileges:
```
sudo aptitude install avant-window-navigator
```
Then you'll have to enter your password.

You can also achieve the same thing by installing avant-window-navigator from System - Administration - Synaptic Package Manager.

Ups, sorry about the missing 'sudo'.

---

### Post by burdock on 2009-02-28
Great! Thanks guys.

---

### Post by zeroemissions on 2009-02-28
Hey, what do you do with the downloaded folder (from the link above) to add new themes??

---

### Post by burdock on 2009-02-28
Go to your appearance preferences (right click desktop>change desktop background) and go to the Themes tab. Just drag the file you downloaded into where the rest of the themes are and it should install.

---

