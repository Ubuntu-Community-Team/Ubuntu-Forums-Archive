---
title: "Thoughts on installing xfwm4 on Lubuntu?"
date: 2021-12-18
forum: Desktop Environments
---

### Post by wrybread on 2021-12-18
I'm running Lubuntu 18 with the LXDE lxpanel 0.9.3 desktop environment and Openbox window manager, and having some problems that don't exist on another system running Mint (Mint 19, DE is Cinnamon 4.0.10, WM is Muffin). I'm wondering if changing the DE or WM (or both) on my Lubuntu system would fix it.

The issue I'm having is that when I run an MPV window as fullscreen it appears on top of windows that are given the "on top" flag. 

For example if I run this command I get an "always on top" small window at the top of the screen:

```
mpv --ontop --no-border --no-osc --no-keepaspect --geometry=1024x96+0+0 ~/test.mp4
```

If I then launch a regular fullscreen window:

```
mpv -fs ~/test.mp4
```

I *should* have a fullscreen window with a small "always on top" window above it, and even if I click on the fullscreen window the "ontop" window should stay in the front. But on my Lubuntu system the fullscreen window will come to the front of the "always on top" window if I click it.

On Mint, however, it behaves properly, and clicking the fullscreen window doesn't bring it in front of the "always on top" window.

For various reasons (it's a long story) I need this functionality on this computer. 

Am I correct in thinking this is a function of the Window Manager? Or is this the Desktop Environment?

Is it reasonably safe to install and then switch to Cinnamon? 

I found this guide:

[https://itsfoss.com/install-cinnamon-on-ubuntu/](https://itsfoss.com/install-cinnamon-on-ubuntu/)

Or would I be much better off with a clean install?

Thanks for any help.

---

### Post by TheFu on 2021-12-18
Support for Lubuntu 18.04 ended.
Support for Xubuntu 18.04 ended.

Move to 20.04 and try either Lubuntu or Xubuntu.

Of the 18.04 flavors, only Gnome3, KDE, and "server" are still supported.

Run **ubuntu-support-status** to see the bad news about all the packages which are unsupported. I'd bet over 50% are NOT.

If you have having GUI issues, start with running a supported release. 20.04 is the current LTS of LXQt that is supported. 21.04 has about 1 month left of support and 21.10 has until July, but 22.04 will be the new LTS in April '22.

You can install any DE that you like on Ubuntu, however, if the DE is in the same "family" as another DE used by the same userid, configuration issues can easily happen. The main families are GTK+ or Qt.  If you don't use either of those, then it is typically a WM-only setup without any DE.  I run without any DE, since my WM, fvwm, provides all that any DE does and more.  When I share my desktop, people always ask what it is. I've been using the same config files for about 20 yrs now, though I did make some side-trips into openbox, fluxbox, Gnome, Mate, LXDE, and XFCE.  Around 2000, I ran KDE for about 6 months.  I have a problem with bloat/inefficient code and seek the most bloat-free environment without being totally hard-core like i3. Being pretty isn't enough.  

Anyway, you can safely use (KDE or LXQt) and 1 of the Gnome DEs (Gnome3, Gnome2, Mate, LXDE, XFCE, Cinnamon) under the same userid. It is when 2 in the same "family" are used that the trampling of config files is problematic.  Just use a different userid for each DE while you test them out and to see which you like for a daily driver.

---

### Post by wrybread on 2021-12-18
Thanks for that. And ugh, I thought I had an LTS version of Ubuntu. When I run "cat /etc/os-release" I get:

```
$ cat /etc/os-release
NAME="Ubuntu"
VERSION="18.04.5 LTS (Bionic Beaver)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 18.04.5 LTS"
VERSION_ID="18.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=bionic
UBUNTU_CODENAME=bionic

```

However when booting the machine does have a "Lubuntu" splash screen, and that's what I installed originally. A couple years ago this machine had a bit of a meltdown when support for that version of Lubuntu ended and I couldn't even run package managers. I forget exactly what I did to fix that, sounds like this might now be regular Ubuntu though?

> Run ubuntu-support-status to see the bad news about all the packages which are unsupported. I'd bet over 50% are NOT.

```
$ ubuntu-support-status
Support status summary of 'wrycade':

You have 2213 packages (66.0%) supported until April 2023 (Canonical - 5y)

You have 93 packages (2.8%) that can not/no-longer be downloaded
You have 1048 packages (31.2%) that are unsupported
```

Thoughts?

> You can install any DE that you like on Ubuntu, however, if the DE is in the same "family" as another DE used by the same userid, configuration issues can easily happen. The main families are GTK+ or Qt. If you don't use either of those, then it is typically a WM-only setup without any DE. I run without any DE, since my WM, fvwm, provides all that any DE does and more. When I share my desktop, people always ask what it is. I've been using the same config files for about 20 yrs now, though I did make some side-trips into openbox, fluxbox, Gnome, Mate, LXDE, and XFCE. Around 2000, I ran KDE for about 6 months. I have a problem with bloat/inefficient code and seek the most bloat-free environment without being totally hard-core like i3. Being pretty isn't enough.

Anyway, you can safely use (KDE or LXQt) and 1 of the Gnome DEs (Gnome3, Gnome2, Mate, LXDE, XFCE, Cinnamon) under the same userid. It is when 2 in the same "family" are used that the trampling of config files is problematic. Just use a different userid for each DE while you test them out and to see which you like for a daily driver.

Thanks so much for that great tutorial, much to digest. And really great tip about using a different username when testing.

---

### Post by Dennis N on 2021-12-18
This output will show Ubuntu for any Ubuntu flavor.
```
$ cat /etc/os-release
NAME="Ubuntu"
VERSION="18.04.5 LTS (Bionic Beaver)"
ID=ubuntu

```
 If you have doubts as to your desktop environment, try in terminal:
```
echo $DESKTOP_SESSION
```
and see what you get. Lubuntu 18.04 with it's default desktop should return LXDE. (I don't have it to check).
It's not 100% LTS. Support is only for packages that are still supported as part of Ubuntu 18.04 LTS.

The command doesn't work in newer releases. Now it is **ubuntu-security-status**. I am using Lubuntu 20.04 here:  
```
dmn@Tyana-vm:~$ neofetch --stdout | grep OS
OS: Ubuntu 20.04.3 LTS x86_64 

```
The status command returns:
```
dmn@Tyana-vm:~$ ubuntu-security-status
1878 packages installed, of which:
1293 receive package updates with LTS until 4/2025
 580 could receive security updates with ESM Apps until 4/2030
   5 packages are no longer available for download

```
Unless I interpret this incorrectly, 585 (68.8%) apparently are getting no security updates now.  So we are not any better off with Lubuntu 20.04.

---

### Post by TheFu on 2021-12-18
> You have 1048 packages (31.2%) that are unsupported

Move to 20.04 with whatever DE(s) you want to try.  The supported packages are from the main Ubuntu release (server/Gnome3) and you happen to be lucky.

Basically, assume 3 yrs of support for any ubuntu LTS flavor with a GUI except the "default" desktop that Canonical is pushing. In 22.04, that default desktop will be Gnome4-based with all the early-use junk it brings. In June, I'll begin testing 22.04 stuff. I did my early adopter stuff in the 1990s.  There are still somethings that I consider broke in 20.04, which is why none of my main machines runs it. It took until the fall of 2020 before netplan was finally good for non-trivial network setups, IMHO.  I'm not a fan of Gnome3 or Wayland. Those break too many of my workflows. With every release since 2010, Ubuntu has always had something wrong - where it didn't "feel" like Unix. 2010 was the last perfect release, IMHO. The base stuff all behaved as expected. No surprises there.  Since that time, Canonical has always added a few zingers to break the OS in every release. 20.04 they broke it by pushing snap packages. At least they didn't try to force Wayland on everyone again.

---

### Post by Dennis N on 2021-12-18
Now on **Ubuntu 20.04** (Not Lubuntu) I get this:
```
dmn@Tyana-vm:~$ ubuntu-security-status
1700 packages installed, of which:
1516 receive package updates with LTS until 4/2025
 181 could receive security updates with ESM Apps until 4/2030
   3 packages are no longer available for download

Packages that are not available for download may be left over from a
previous release of Ubuntu, may have been installed directly from a
.deb file, or are from a source which has been disabled.
For more information on the packages, run 'ubuntu-security-status
--unavailable'.

Enable Extended Security Maintenance (ESM Apps) to get 10 security
updates (so far) and enable coverage of 181 packages.

This machine is not attached to an Ubuntu Advantage subscription.
See https://ubuntu.com/advantage

```
So even now, with this LTS, there are 10 security updates I cannot get unless I subscribe to ESM.

---

### Post by wrybread on 2021-12-18
Thanks for all the tips. This machine is running in an old arcade cabinet, and I'd like to put an OS on it that I can "set it and forget it" for a decade or two. Running regular updates is fine, but I don't want to have to update the entire OS every few years if I can avoid it.

Is there some Linux version that would make that possible?

---

### Post by Dennis N on 2021-12-18
> **wrybread said:**
> Thanks for all the tips. This machine is is running in an old arcade cabinet, and I'd like to put an OS on it that I can "set it and forget it" for a decade or two. Running regular updates is fine, but I don't want to have to update the entire OS every few years if I can avoid it. **Is there some Linux version that would make that possible**?
Do you mean you don't want to reinstall the OS? 
If so, then you could look for a "rolling release" - I am familiar with Manjaro Linux which is a rolling release (I have it installed in my multiboot setup), and there are probably others. All packages are updated as newer versions appear. But even Ubuntu you don't need to reinstall - it can be updated to a newer release version by doing a "distribution upgrade".

---

### Post by guiverc on 2021-12-18
Ubuntu 18.04 LTS has 5 years of *standard* support; however *flavors* of Ubuntu came with only 3 years.

ie. read a release notice for [Ubuntu 18.04.5]("https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/") and you'll read

> Maintenance updates will be provided for 5 years for Ubuntu Desktop,  Ubuntu Server, Ubuntu Cloud, and Ubuntu Base.  All the remaining  flavours will be supported for 3 years.

You'll note I used the older 18.04.5 notice, rather than the latest 18.04.6; that was because the [later 18.04.6]("https://fridge.ubuntu.com/2021/09/17/ubuntu-18-04-6-lts-released/") occurred after *flavors* had reached EOL and thus the notice didn't apply to them.

You can us the command `ubuntu-support-status` on an existing install to see the security status of your system.

FYI:   In diagnosing details with Lubuntu (*which has been LXQt only for many releases now*) I regularly replace `openbox` with others (inc. `xfwm4`) to find out if issues relate to `openbox` which does have some issues on specific screen layouts in my experience. 

But note I only *scanned* your post, as there is no Lubuntu 18 (*Ubuntu uses the year format only for snap only products such as Ubuntu Core 18; Lubuntu is a deb based product so it's a year.month format release*) and LXDE is unsupported by Lubuntu (*having been so since [2021-April]("https://lubuntu.me/bionic-eol/") when 3 years from release was reached just as with all flavors*), with the [oldest supported Lubuntu release currently being Lubuntu 20.04 LTS]("https://lubuntu.me/lubuntu-20-10-end-of-life-and-current-support-statuses/").

Ubuntu 18.04 LTS with LXDE **is** still supported, but it's not Lubuntu, and only parts of your system are now covered by security patches/fixes which you can confirm using the aforementioned `ubuntu-support-status` command.

---

### Post by Dennis N on 2021-12-18
> All the remaining flavours will be supported for 3 years. 

I was just looking at Lubuntu 20.04, and am a bit puzzled on how 3 years support fits into this summary:

```
dmn@Tyana-vm:~$ ubuntu-security-status
1878 packages installed, of which:
1293 receive package updates with LTS until 4/2025
 580 **could** receive security updates with ESM Apps until 4/2030
   5 packages are no longer available for download

Packages that are not available for download may be left over from a
previous release of Ubuntu, may have been installed directly from a
.deb file, or are from a source which has been disabled.
For more information on the packages, run 'ubuntu-security-status
--unavailable'.

[U]Enable Extended Security Maintenance (ESM Apps) to get 10 security
updates (so far) and enable coverage of 580 packages[/U].

This machine is not attached to an Ubuntu Advantage subscription.
See https://ubuntu.com/advantage

```
As to the underlined sentence, it seems to be saying that I must subscribe to ESM to get the 10 current security updates? And thereafter this subscription will include any future security updates for the 580 packages (30.8%)? Otherwise, these 580 packages have NO security support, even though three years have not passed since the release date.

---

### Post by guiverc on 2021-12-18
> **Dennis N said:**
> I was just looking at Lubuntu 20.04, and am a bit puzzled on how 3 years support fits into this summary:

-- snipped

As to the underlined sentence, it seems to be saying that I must subscribe to ESM to get the 10 current security updates? And thereafter this subscription will include any future security updates for the 580 packages (30.8%)? Otherwise, these 580 packages have NO security support, even though three years have not passed since the release date.

I personally found the output from `ubuntu-support-status` much easier to read, however others didn't & raised issues, thus it's retiring & replacement with `ubuntu-security-status` on more recent releases.

I can only give ***opinion*** here, as I've not used ESM as I've see no need to (*and have 50 machines I can still use it due Ubuntu membership*).

During the current state of 20.04 where *standard* support still applies; you'll get no benefit of ESM. I see the message is *marketing* related* &* trying to **up-sell** you on ESM now even though you won't benefit until after 2025-April.. You have 10 security updates that you currently would miss out on IF it was May-2025 & didn't have ESM enabled...  **Please note: **I'd have to look at the code to be sure, but I've no intention of that - thus I could be wrong.

*I got interrupted as I wrote this by a indicator that my write of today's Lubuntu focal daily has completed, so I can run some QA-tests on it & update from focal boxes via 'upgrade via re-install' ([install using existing partition using Lubuntu terminology]("https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743")) thus performing the upgrade of packages at the same time as a QA-test, & not lose my files, packages etc if all goes as planned..  I may look at what I see on my boxes if I think of it, and may have more.. but also risk forgetting about it until after I've turned the box off to complete the QA-test (and I won't turn a box back on until it's needed)...*

---

### Post by TheFu on 2021-12-19
> **wrybread said:**
> Thanks for all the tips. This machine is running in an old arcade cabinet, and I'd like to put an OS on it that I can "set it and forget it" for a decade or two. Running regular updates is fine, but I don't want to have to update the entire OS every few years if I can avoid it.

Is there some Linux version that would make that possible?

No.  If you want 10 yrs of support, buy a RHEL Server license for $900.
However, inside Redhat, everyone runs Fedora for their desktops.

There is the option for 3 machines, to give up a little privacy and gain 10 total years of support from release by signing up for ESM. Individuals get 3 machines for free.  Ubuntu Members get 50 machines for free.  There is a paid option too.

However, having a system untouched for 10 yrs has proven to be a terrible way to handle critical needs, since people forget what they did 10 yrs ago - heck, even 5 yrs is bad for not touching a system, if it is the only box of the same type.  I use Ubuntu almost everyday and have a few 18.04 servers still, but have a slight fear of moving them to 20.04 or 22.04 because of the changes to important software that they run.  
I think 2 yrs is optimal. 4 yrs is a stretch and after 4 yrs, it is like a leaky roof (any OS), that won't ever get better, just worse.  The choices are pay-me-now or pay-me-much-more-later - pay will be either lots of time because things change drastically every 4 yrs or hardware breaks and needs replacement on the HW schedule, not yours.  Loading an OS and getting all the daily maintenance stuff setup every 2-4 yrs does something to keep an OS running problem free for longer that install-and-forget doesn't accomplish.

I see that you've added above this is a gaming system in a special-made console case. If it isn't networked at all, perhaps it runs old Atari 2600 or other old game-center stuff that isn't networked, then I probably wouldn't update **ever** after I got Asteriods, Yars Revenge and Spy Hunter working, I'd stop and never touch it again until forced to do so.  I'd have excellent backups, so that anything short of a MB failure wouldn't force any fresh install.

IMHO.

---

