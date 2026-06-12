---
title: "GDM3 starting weird desktop"
date: 2019-07-07
forum: Desktop Environments
---

### Post by maggielostkeys on 2019-07-07
Hi all,
(Sorry if this is a duplicate, I couldn't find this anywhere)

I recently installed Ubuntu Desktop on my Ubuntu 18.04.2 Server. My goal was to get a thing alla Raspbian going (boot into console, start desktop once logged in from console).
The problem is, that GDM3 starts a slightly different version of GNOME when using 'startx'. It pretty much looks the same, but has additional or missing features compared to the "normal" desktop release.

e.g.:
- moving the cursor into the upper-left corner opens a see-all-windows overlay (don't know what thats called)
- missing dock
- missing settings
- max and min buttons not enabled by default

When I have to go in through the GDM3 login however, (after restarting the GDM3 service or booting directly into the GUI, etc.) I end up in the "normal" desktop version.

Any ideas?

Edit: Ok, so it turns out it WAS the Unity Desktop. I got confused because that&#8217;s the one specifically didn&#8217;t want and configured GNOME as my standard desktop. This doesn&#8217;t seem to work though.

---

### Post by DuckHook on 2019-07-13
Welcome to the forums, maggielostkeys.

We have no idea how you ended up with the Unity DE alongside Gnome3. A wild guess would be that you've tried multiple installs on your initially pristine server. Another possibility: was it actually the server ISO you installed or did you, in fact, install the DE version? Further: did you network upgrade to 18.02 from a previous version or was it a pristine install?

As you can see, the devil is in the details.

If you want Gnome3 to start each time, there are a few ways to do this:

[LIST=1]
[*]One way is to install *gdm* as your display manager. This will allow you to set Gnome3 as your default DE by choosing it the first time. Thereafter, it should just default to Gnome3 until you choose Unity again.
[*]Another way is to reinstall the whole server OS, but this time, taking pains to avoid adding Unity afterwards and add only Gnome3.
[*]A third way is to install the full graphical ISO, since you apparently want the GUI to run on top of the server install anyway.
[/LIST]
Without more background, context and an understanding of what and why you want to achieve certain goals, it is rather difficult to guess which way you should go.

---

### Post by PaulW2U on 2019-07-14
> **maggielostkeys said:**
> - moving the cursor into the upper-left corner opens a see-all-windows overlay (don't know what thats called)
- missing dock
- missing settings
- max and min buttons not enabled by default

I don't think Unity has been installed but you are seeing a slightly different looking GNOME Shell when not logging in in the conventional way.

What you describe is what I see when first starting a **GNOME** session rather than an **Ubuntu** session. A GNOME session, which can be selected at log-in after installing 'vanilla-gnome-desktop' removes various Ubuntu-like features and customisations. It's how GNOME Shell appears in other distributions such as Fedora and it's how Ubuntu GNOME would look like if it still existed as a separate flavour. 

I've deliberately set up many installations of Ubuntu this way and a missing dock, and lack of maximise and minimise button are the first things that I add back. Moving the mouse pointer to the to the top left hand corner of the screen to display the Activities Overview is also standard behaviour in GNOME Shell.

I'm not saying that you have installed 'vanilla-gnome-desktop' but I'm sure that somehow the wrong session is being started.

---

### Post by cruzer001 on 2019-07-14
I use the server iso to install [Gnome]("https://packages.ubuntu.com/bionic/gnome") and it does sound like your running that when using startx.
```
echo $XDG_CURRENT_DESKTOP
```
That will verify what desktop you are running.

---

### Post by maggielostkeys on 2019-07-14
Hi,
Thank you for your answers.

I originally installed Ubuntu (Server) 18.04.2 and used *ubuntu-desktop *to get the DE later on. gdm3 is set to default; I uninstalled lightdm.
(@DuckHook: My mistake. Unity is available in that drop-down menu on the gdm3 login screen, but isn't used here.)

Quickly checked with @cruzer001's idea and @PaulW2U seems to be right:[I]
startx [/I]defaults to "GNOME" while a direct boot into the DE (or login through, starting or restarting gdm3) defaults to "ubuntu:GNOME" <-- That one I want


I just couldn't find an option to select "ubuntu:GNOME" as my default anywhere. Though it is my default on the gdm3 login screen, it doesn't start when running *startx*.

Any ideas? Thanks for taking the time.

---

### Post by CatKiller on 2019-07-14
[https://unix.stackexchange.com/a/243210](https://unix.stackexchange.com/a/243210)

---

### Post by cruzer001 on 2019-07-14
Yes, create a ~/.xinitrc file with the command to start ubuntu-gnome session.  Not sure what the proper command is for a ubuntu-gnome session.  Perhaps someone else can tell us or just do a bit of experimenting.  I believe it is located in /usr/bin.

[https://wiki.archlinux.org/index.php/Xinit](https://wiki.archlinux.org/index.php/Xinit)

---

