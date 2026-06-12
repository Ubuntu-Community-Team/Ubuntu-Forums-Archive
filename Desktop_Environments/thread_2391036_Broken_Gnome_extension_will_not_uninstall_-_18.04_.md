---
title: "Broken Gnome extension will not uninstall - 18.04 full release"
date: 2018-05-05
forum: Desktop Environments
---

### Post by felgro on 2018-05-05
[COLOR=#0000ff]*[Note - I actually fixed this as I was writing, but I'll post it anyway for others that may have same problem]*[/COLOR]

First up, I gotta say 18.04 is an order of magnitude better than 16.04 was for me. But, as always, there are surprises popping up where you least expect them. My gremlins are doing crazy stuff in gnome shell extensions - which have turned out to be like playing Russian roulette. Most work, a lot are broken and the one that has brought me here is broken and welded in place that way. It's the "Applications Menu" applet - it has installed in a failed state, won't say why, is stuck in top left of top bar and does nothing on mouse click or hover. It initially broke my "Activities" item, but that eventually returned and is placed to the right of it -

[IMG]https://kek.gg/i/5jrrBc.jpg[/IMG]

Below is how it appears in Tweaks and at the gnome site -

[https://extensions.gnome.org/extension/6/applications-menu/](https://extensions.gnome.org/extension/6/applications-menu/)

[IMG]https://kek.gg/i/39W2YT.jpg[/IMG]

It's just stuck - neither extension managers do anything. Similar issue was logged with the alpha release here -

[URL="https://ubuntuforums.org/showthread.php?t=2382538"]https://ubuntuforums.org/showthread.php?t=2382538
[/URL]
Previous fixes -

[URL="https://ubuntuforums.org/showthread.php?t=2356762&p=13625608#post13625608"]https://ubuntuforums.org/showthread.php?t=2356762&p=13625608#post13625608
[/URL]
have said all you need to do is delete the applet folder from -

```
~/.local/share/gnome-shell/extensions/
``` 

and reboot. This information is wrong. 

a) You don't need to reboot. Just log out of your session and log back in, and

b) the correct location to delete the applet folder from is -

```
/usr/share/gnome-shell/extensions
```

- and you need root to do so.

Hope this saves somebody some time.

---

### Post by deadflowr on 2018-05-05
Ubuntu can install extensions from the software center and one particular package *gnome-shell-extensions* provides several extension into a single package.
On top of that package are several other, more directly named, packaged extensions for Ubuntu:
(See: [https://packages.ubuntu.com/search?suite=bionic&section=all&arch=any&keywords=gnome-shell-extension&searchon=names]("https://packages.ubuntu.com/search?suite=bionic&section=all&arch=any&keywords=gnome-shell-extension&searchon=names"))
You can see the same list, roughly, with
```
apt search gnome-shell-extension
```

Nothing added from the extensions web page should place anything in the /usr directory.
Those should all be in the .local directory.
so it's best to see where which was installed from before deleting files.
As deleting the files may end up breaking the systems package manager.
If those extensions were indeed from Ubuntu's software repositories.

---

### Post by monkeybrain20122 on 2018-05-05
Just go to .local/share/gnome-shell IIRC there is a subfolder where these extensions are. Just delete it and restart gs

---

### Post by kerry_s on 2018-05-05
it's better to use the extension site for extensions. make sure you click the version button to check if your gnome-shell version is listed, i think it's 3.26 in 18.04
if your version is not listed, you can click on the web site link, some times they don't upload the newest version yet. it's a bit of a pain installing manually though, i usually just skip extensions that are not updated.

you can do "gnome-shell --version" to double check what your running.
[ATTACH=CONFIG]279584[/ATTACH]

---

### Post by Dennis N on 2018-05-05
The Applications Menu (by fmuellner) in your post #1 does work in 18.04. See screenshot. Maybe you turned off the Activities Overview hot corner in upper left? It needs to be on. A button for Activities Overview is then at the bottom of the menu.

---

### Post by felgro on 2018-05-06
> **deadflowr said:**
> Nothing added from the extensions web page should place anything in the /usr directory.
Those should all be in the .local directory.

Nope, not in this case. Extensions do write to .local as well, but they also write to /usr - in the case of "Applications Menu", it writes and loads from the /usr location. Deleting .local entry does NOT remove it. You need to delete it from /usr and restart session to get rid of it. Have a look at both locations - I think extension authors are writing to one, the other or both and don't tell anybody what they've done or what their extension is doing.

---

### Post by deadflowr on 2018-05-07
> **felgro said:**
> Nope, not in this case. Extensions do write to .local as well, but they also write to /usr - in the case of "Applications Menu", it writes and loads from the /usr location. Deleting .local entry does NOT remove it. You need to delete it from /usr and restart session to get rid of it. Have a look at both locations - I think extension authors are writing to one, the other or both and don't tell anybody what they've done or what their extension is doing.

Probably misread what I posted, but those extensions were more likely installed through an apt package and not from the web.
An apt package will write to the /usr directory.
But the version installed from the web will not. And can not without a serious security concern.
(To write to /usr the file must be able to access root which gnome extensions web site does not have open access to, and I have never seen it ask for those rights in the nearly 6 years of using gnome shell)

In these cases you have to ignore what the web page tells you (in terms of being able to update ) as the app is locked down to the version built for the particular package for the particular version of Ubuntu you have.
If you have an issue with the apt packaged version you can file a bug against it.


If you would like to not use the apt package version and instead would like to use the web version you can usually just remove the package.
However in your case that might not work right as you have now removed related files and apt scuffs at that sometimes.
In these cases it is best to run a reinstall of the package first, then run the remove.

After you remove the package all the extensions from it can be installed (and controlled) through the extension page as you would probably like it to.

Hope that makes more sense.

---

### Post by PaulW2U on 2018-05-07
> **felgro said:**
> You don't need to reboot. Just log out of your session and log back in
**Alt+F2** and entering **r** is an even quicker way to restart.
> **Dennis N said:**
> Maybe you turned off the Activities Overview hot corner in upper left? It needs to be on.
Thanks for this confirmation.
> **deadflowr said:**
> After you remove the package all the extensions from it can be installed (and controlled) through the extension page as you would probably like it to.
**gnome-shell-extensions** contains a basic set of extensions that can't be removed if **vanilla-gnome-desktop** has been installed but for those that have kept the traditional Ubuntu look it's not a problem.

Anyway thanks felgro, Dennis N and deadflowr, as a result of reading this thread I've revisited my extensions and have solved most of my issues. At least I can now use the Applications Menu which I haven't seen for some time. :)

---

### Post by deadflowr on 2018-05-07
> gnome-shell-extensions contains a basic set of extensions that can't be removed if vanilla-gnome-desktop has been installed but for those that have kept the traditional Ubuntu look it's not a problem.
Then probably best to try reinstalling the package and leave it as is and not try to remove if vanilla gnome is indeed installed.
(Or reinstall it and then disable those extensions you would not want to use.)

Good to know that the extensions package is a part of vanilla, though.
I did not even think of that.

---

### Post by PaulW2U on 2018-05-07
> **deadflowr said:**
> Then probably best to try reinstalling the package and leave it as is and not try to remove if vanilla gnome is indeed installed.
(Or reinstall it and then disable those extensions you would not want to use.)

Good to know that the extensions package is a part of vanilla, though.
Yes, I reinstalled that package, switched on "Activities Overview Hot Corner" and both of my Ubuntu installations can now use the Applications Menu.

---

### Post by Dennis N on 2018-05-07
The Ubuntu 18.04 fresh install had only two extensions and they were the "system extensions". I installed all new extensions from the Gnome extensions web site, including the Applicatiions Menu being discussed. Just switch the extension activation switch to "on" and a confirmation box pops up for installing. It appears immediately. To use the site for managing your extensions, you need to first take the two steps that are given on the main page.

---

### Post by PaulW2U on 2018-05-07
> **Dennis N said:**
> The Ubuntu 18.04 fresh install had only two extensions and they were the "system extensions". I installed all new extensions from the Gnome extensions web site, including the Applicatiions Menu being discussed. Just switch the extension activation switch to "on" and a confirmation box pops up for installing. It appears immediately. To use the site for managing your extensions, you need to first take the two steps that are given on the main page.
I know how to use the extensions website, I've been using it for some time, but I have **vanilla-gnome-desktop** added to my installation to give me a more traditional GNOME look and feel. This automatically installs several extensions including the Applications Menu. I still have a few errors that I haven't yet resolved including one with the Places Menu which is also installed automatically.

I see there is an update pending to the Applications Menu which presumably can't be installed as here it is a system extension. The menu is working but I would imagine I can't use the latest version from the website and will have to wait for the **gnome-shell-extensions** package in the repositories to be updated.

---

### Post by deadflowr on 2018-05-07
> I see there is an update pending to the Applications Menu which presumably can't be installed as here it is a system extension. The menu is working but I would imagine I can't use the latest version from the website and will have to wait for the gnome-shell-extensions package in the repositories to be updated.

Is the update notification from tweaks or the web page?
(Or both)

---

### Post by PaulW2U on 2018-05-07
> **deadflowr said:**
> Is the update notification from tweaks or the web page?
From the web page. If I try to update then I get an error until I restart gnome-shell and redisplay the web page. Then I see the update notification again. The error also then appears in Tweaks.

And now the error has gone and no update showing. :confused:

Off to do something less taxing on the brain. Thanks all.

---

### Post by deadflowr on 2018-05-07
You probably now have the apps-menu extension duplicated in both the /usr directory and .local directory locations.
I think it can be one or the other but not both.
Can probably just delete it from the .local directory.
Might require a restart (gnome restart not system reboot) for the Error tag to clear up.

It would be nice if those extensions provided by the apt package would get the grayed out affect that the Ubuntu Dock and Ubuntu Appindicator extensions do on the web page.
Probably can't though since those two are Ubuntu built specifically and do not have corresponding versions/whatever-you can-call-it at the web page, me thinks.

random thoughts
random thoughts

---

### Post by Dennis N on 2018-05-07
I didn't know there was a vanilla-gnome. I've used Fedora Gnome in the past and I imagine it is probably like that. I like the way Ubuntu has done things in their regular GNOME, so I'm a happy camper. Reading the previous comments, I'm also now glad I am using the website to manage the extensions.

---

### Post by deadflowr on 2018-05-07
Rebooting back into a system that I have the gnome-shell-extensions package installed on it's easy to see which is from the package (or Ubuntu) and which is not
The ones from the web page all have an X to remove and those from Ubuntu do not.
Also, all the extensions from Ubuntu have updates pending. :icon_frown:

---

### Post by PaulW2U on 2018-05-07
> **deadflowr said:**
> You probably now have the apps-menu extension duplicated in both the /usr directory and .local directory locations.
I think it can be one or the other but not both.
I **do** have the extension in both directories but I no longer see an error or update pending so I'm not deleting anything. :)
> **Dennis N said:**
> I didn't know there was a vanilla-gnome.
I see what Ubuntu GNOME would look like if it still existed.
> **deadflowr said:**
> The ones from the web page all have an X to remove and those from Ubuntu do not.
This evening I've managed to update all of my extensions even those that were initially installed by Ubuntu. Most of them now have the X. This includes the app-menu which is no longer tagged as being a system extension. So I'm thinking that the local version of an extension should override a system version provided that it is newer but that's not consistent with the errors that I have been experiencing over the last few months.

---

