---
title: "Seduced By Fedora; Want Stock Gnome Shell On 12.04"
date: 2012-06-01
forum: Desktop Environments
---

### Post by buzzingrobot on 2012-06-01
I wandered off the path and installed Fedora 17 a couple of days ago when it was released.  It's very nice. 

Fedora 17 runs an essentially stock Gnome 3.4.2, with no tweaking of Gnome Shell that I can  discern. 

I'm going to return to Ubuntu but it would really be nice if I could install the same stock Gnome 3.4.2 on it.  i've installed Gnome Shell, etc., on 12.04 before and it retained the theme and color scheme of Unity.  I want to avoid that and use the "out of the box" Gnome theme and colors.

I see a Gnome Shell Remix exists, but that seems to come with a lot of caveats about updates, etc.

I don't care if Unity/HUD remain or not.  What I'm interested in is Gnome Shell on Ubuntu with no problems down the road about updates or other issues. 

Is a minimal install, followed by Gnome from the Gnome team's PPA, a rational approach?  Is there a risk that sooner or later I'll pull in dependencies that overlay Unity/HUD on the shell?

---

### Post by Cheesemill on 2012-06-01
I just use standard Ubuntu and install the gnome-shell package. The only difference between that and stock Gnome Shell is the theme but you can easily change back to Adwaita (the stock theme) in a couple of seconds using gnome-tweak-tool.

The only other difference I can think of is that you will be using LightDM instead of GDM as your logon screen, but I actually prefer the way that LightDM integrates with the desktop background.

Is there anything else not stock about Ubuntu + gnome-shell that I've missed?

---

### Post by buzzingrobot on 2012-06-01
> **Cheesemill said:**
> I just use standard Ubuntu and install the gnome-shell package. The only difference between that and stock Gnome Shell is the theme but you can easily change back to Adwaita (the stock theme) in a couple of seconds using gnome-tweak-tool.



Thanks! That's good to hear. I'm off to burn a USB stick.

---

### Post by Frogs Hair on 2012-06-01
Evolution Mail & Calendar , Gnome Desktop Utilities, and Tomboy Notes can be installed from the software center.

---

### Post by buzzingrobot on 2012-06-01
Installed, theme changed, tweaked, and adding software. Thanks!

---

### Post by hictio on 2012-06-01
> **buzzingrobot said:**
> I wandered off the path and installed Fedora 17 a couple of days ago when it was released.  It's very nice. 

Fedora 17 runs an essentially stock Gnome 3.4.2, with no tweaking of Gnome Shell that I can  discern. 

I'm going to return to Ubuntu but it would really be nice if I could install the same stock Gnome 3.4.2 on it.  i've installed Gnome Shell, etc., on 12.04 before and it retained the theme and color scheme of Unity.  I want to avoid that and use the "out of the box" Gnome theme and colors.

I see a Gnome Shell Remix exists, but that seems to come with a lot of caveats about updates, etc.

I don't care if Unity/HUD remain or not.  What I'm interested in is Gnome Shell on Ubuntu with no problems down the road about updates or other issues. 

Is a minimal install, followed by Gnome from the Gnome team's PPA, a rational approach?  Is there a risk that sooner or later I'll pull in dependencies that overlay Unity/HUD on the shell?

What caveats about updates do you mean?
AFAIK it is based on plain vanilla Precise Pangolin 12.04 so the same rules should apply, updates for 5 years, right?

---

### Post by CharlesA on 2012-06-01
> **hictio said:**
> What caveats about updates do you mean?
AFAIK it is based on plain vanilla Precise Pangolin 12.04 so the same rules should apply, updates for 5 years, right?
Aye. 5 years of support.

---

### Post by hictio on 2012-06-01
I've been testing it -I mean Gnome Shell Remix- on a Thinkpad T43 (2 GB RAM) for a week or so, and I really, really like it.
I was thinking in giving Linux Mint (Cinnamon) a try, and if the thing doesn't do it for me, go with Gnome Shell Remix (12.04, of course) for good.
At the moment I'm running Gnome 3 ontop of a plain vanilla Precise Pangolin install, and pretty much goes A Ok, but I wouldn't mind re-installing from scratch Gnome Shell Remix in order to get a cleaner and leaner base install for the upcoming 5 years.

---

### Post by wraith2k on 2012-06-02
Quick question, I also wanted stock Gnome 3, but decided to get rid of unity so after removing it I did a sudo apt-get install gnome-core and selected gdm and restarted when it was done, but after booting up it wasn't themed like Fedora 17. Any idea to get the themed gdm?

---

### Post by buzzingrobot on 2012-06-02
> **hictio said:**
> What caveats about updates do you mean?
AFAIK it is based on plain vanilla Precise Pangolin 12.04 so the same rules should apply, updates for 5 years, right?

Just a concern that some Ubuntu-modified code added during an update might break Gnome.

The LTS aspect? I'll almost certainly replace this with 12.10, probably during the beta cycle.

---

### Post by hictio on 2012-06-02
> **buzzingrobot said:**
> Just a concern that some Ubuntu-modified code added during an update might break Gnome.

The LTS aspect? I'll almost certainly replace this with 12.10, probably during the beta cycle.

Get your point, thanks.
Personally, I'm not interested in switching to not LTS releases, I'll stick to Precise for the next years :)
According to the [12.04 release notes](http://ubuntu-gs-remix.sourceforge.net/p/release-notes/release-notes-1204/), the author does recognize problems upgrading to newer releases.

---

### Post by topyli on 2012-06-23
I think I'm pretty close to vanilla GNOME here.

The basics: gnome-shell, gnome-themes-standard, gnome-backgrounds. Change theme and background to get the Adwaita look.

The new GNOME 3 apps: gnome-documents, gnome-contacts, gnome-sushi, epiphany-browser & epiphany-extensions (now rebranded as 'Web').

Other gnomish additions you may want: evolution, tracker & tracker-search-tool, tomboy, possibly others.

You may want to add the GNOME Team's PPA in order to get up-to date and missing standard GNOME packages. Precise is missing some and is using 3.2 versions of others (such as Totem, IIRC). [https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)

You will not get the GDM experience you have in Fedora. Debian and Ubuntu still ship GDM 3.0 and packaging any later GDM for Debian still seems to be unsurmountably difficult for some reason.

---

### Post by kohoutek1 on 2012-06-24
> **buzzingrobot said:**
> 

I see a Gnome Shell Remix exists, but that seems to come with a lot of caveats about updates, etc.



Yes, there are some noticeable caveats with the extensions. You'll need to watch those carefully, especially during upgrades, though problems will be rare during updates. 

The Shell itself won't "break," but if you depend a lot on extensions, you may need to clean them out and start with fresh installations from time to time so that you can keep whatever user habits you've established.

---

