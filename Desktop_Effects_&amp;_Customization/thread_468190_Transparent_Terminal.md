---
title: "Transparent Terminal?"
date: 2007-06-08
forum: Desktop Effects &amp; Customization
---

### Post by WaeV on 2007-06-08
I have seen many pictures of people's desktops with a transparent terminal and white or green text instead of the default black-on-white text editor style.  Does anyone know how I can achieve this?

example:
[http://felipe-alfaro.org/blog/wp-content/Ubuntu-Edgy-AIGLX-Beryl.png](http://felipe-alfaro.org/blog/wp-content/Ubuntu-Edgy-AIGLX-Beryl.png)

Is this a beryl theme or what?

---

### Post by NeoLithium on 2007-06-08
Well, gnome-terminal has a pseudo transparency available in the profile options. It's in EDIT -> Current Profile -> Effects.  For true transparency, you might need to check out Beryl, just take a quick search through the forums iwth the keywords'How to Beryl'

Hope this helps! :)

---

### Post by WaeV on 2007-06-08
Thanks that's exactly what I was looking for.

---

### Post by Yoooder on 2007-06-08
Beryl is not a theme, it is a 3D driven window manager (replacing Metacity from GNOME).  **It should be noted that it is still an unstable project** and is prone to some crashes--but many people have good luck using it.

Gnome-terminal (at least last time I checked) does not support true transparency, even with Beryl.  The catch is that there is either a patch or a custom version of gnome-terminal that fixes the issue preventing proper transparency.

There is a less eye-pleasing option built into gnome-terminal's session options that allow for what it calls transparency.  The difference between gnome-terminal's transparency and "true" transparency is that gnome-terminals always shows the desktop under the app, not other applications.

---

### Post by WaeV on 2007-06-10
Yeah I meant a theme for emerald.  Beryl is working pretty darn well.

---

### Post by Nythain on 2007-06-11
a lot of those screenshots might also be using eterm or aterm also... not sure where you are looking

in that exact screenshot that looks more than likely like one of beryls settings, you can make anything and everythign almost truly transparent in beryl... if it wasnt so buggy and resource consuming id still be using it, but untill then its kde's pseudo transparency for me

---

### Post by Sweet Mercury on 2007-06-11
> **WaeV said:**
> I have seen many pictures of people's desktops with a transparent terminal and white or green text instead of the default black-on-white text editor style.  Does anyone know how I can achieve this?

example:
[http://felipe-alfaro.org/blog/wp-content/Ubuntu-Edgy-AIGLX-Beryl.png](http://felipe-alfaro.org/blog/wp-content/Ubuntu-Edgy-AIGLX-Beryl.png)

Is this a beryl theme or what?

You can get halfway there with Gnome-terminal. Xfce4-terminal is much more customizable.

In my attachment, the window on the left is Gnome-terminal, on the right is Xfce4-terminal

edit: This is all just using Metacity.

---

### Post by Dasugo on 2007-06-13
thanks NeoLithium... I don't need to go all out with compiz or Beryl so this works perfectly for me.:p

---

### Post by GV1pJTHl on 2007-07-12
Sweet Mercury, on your screenshot will it again only show the background image or is there a setting to make it truly transparent?

---

### Post by Lividity on 2007-08-23
From the terminal:

sudo apt-get install aterm

nano ~/.Xdefaults

# Copy and paste the following text into .Xdefaults:

  aterm*loginShell:true
  aterm*transparent:true
  aterm*shading:60
  aterm*background:Black
  aterm*foreground:White
  aterm*scrollBar:true
  aterm*scrollBar_right:true
  aterm*transpscrollbar:true
  aterm*saveLines:32767
  aterm*cursorColor:Red
  aterm*font:*-*-fixed-medium-r-normal--*-140-*-*-*-*-iso8859-1
  aterm*boldFont:*-*-fixed-bold-r-normal--*-*-140-*-*-*-*-iso8859-1

# aterm is transparent after rebooting.

[http://hidebehind.com/5D957A]("http://hidebehind.com/5D957A")

---

### Post by vorlon on 2007-09-13
just wanted to say thanks to Lividity, for posting that config up.

That helped me what I wanted to achieve with aterm! appreciate it

---

