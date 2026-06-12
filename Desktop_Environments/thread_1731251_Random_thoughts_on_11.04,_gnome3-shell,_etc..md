---
title: "Random thoughts on 11.04, gnome3-shell, etc."
date: 2011-04-16
forum: Desktop Environments
---

### Post by promet on 2011-04-16
Hi.

After having been unable to wait for the later full release of Natty I, maybe a little foolheartedly, "burned down" my 10.10 install (which had been several upgrades of previous releases installed "over" one another) to install the Natty Beta, "fresh".

I'll have to say though, on the whole, I'm pretty impressed. Soon after the 11.04 install, I installed Gnome3 (gnome-shell). I was pretty disappointed that, once installed, it "broke" the Ubuntu (Unity) and Ubuntu Classic managers, for me at least, that came with the standard install, and though they're cropping up now, I don't think that, at the outset, that there was a substantial enough disclaimer about this by Gnome. I was really hoping to get to use them side-by-side and learn about and compare them all. It's unfortunate that this isn't currently possible.

Since it's a new install, and I just want to "use" Natty, I won't be going through the trouble of re-enabling the other sessions immediately. I hear there was some "contention" over the window manager changes to this release. I wish though, that the organizations could have seen eye-to-eye on this one. I mean, I run a pretty middling machine:



[IMG]http://prometx.homelinux.org/images/system-info.png[/IMG]



And, I think I can say (usual "beta-issues" notwithstanding) that I am noticing significant performance advantages on this machine. I'm kind of in nerd-pig heaven, actually. So, I hope this can get sorted, because (he says, in his naive, romantically-notioned way) that we should be exploring this excellent system unrestrained, from all perspectives, so that we can really push it to its better potential.

Gnome3? Mehhhhh, it's pretty slick though, and the more I use it, the more I begin to "get it", rather than be frustrated by my ideas of what it's "supposed to do". On the whole, I have to say, it's meeting some pretty fetching requirements for me just now. I just wish I could see this release from "all angles", you know?

I'd appreciate hearing from some of you, if you've got any thoughts along this line, what do you think?

At any rate, Huzzah!

---

### Post by HeavyAl on 2011-04-17
I'm responding to this on the Ubuntu 11.04 beta 2 install, having ripped out Unity and parked Gnome 3 in its place. Unity was a complete dismantlement to me! I tried Gnome 3 on Fedora 15 alpha and OpenSUSE - both of those distros showed Gnome 3 as it is supposed to be; clean, smooth, and fast! Having to run through Ubuntu Natty install through the blender to get Gnome 3 to work on it has left a bad taste in my mouth. 

Gnome 3: You've got a very minimal approach to locating everything and the interface is never in your way - its just a bar across the top that responds when you run your mouse over it in a way that just makes sense. New workspaces are added as you run applications. The new nautilus is solid as a rock and takes care of everything you need to do with your files all in one place. Yeah, theres a lot of fun stuff that is missing right now but overall the presentation you get with Gnome 3 is a heavenly experience.

Unity: CLUNKY, thats the word that first came to mind when I pulled it up after install Natty. I can't believe this thing is considered ready - its about as ready as KDE4 was when it was first introduced. The menu system is inconsistent and actually causes screen flicker when you run your mouse over the file menu on the top left. The bar running vertically across the left side of the screen is ugly at best and the tiny arrows on them do very little to indicate that an app is actually open. And again as so many others have said prior to this release the buttons for windows being on the top left is a ridiculous 'innovation' that adds nothing useful to the user experience. Overall I'm rather disgusted with it, but then Linux is about choice so your mileage will of course vary.

---

### Post by pony-tail on 2011-04-17
I hated Unity !
Gnome 3 I can live with if I have to but I am having application crashes from time to time . enough to be annoying . I would not at this time have either as the only OS .
I too have found that Gnome 3 breaks unity - it is only a test install so I am not concerned .
At this stage I prefer Gnome 2.3x and panels - or even ( god forbid ) Windows 7 or Vista to Unity and Gnome 3 . And that as a full time Linux user .

---

### Post by timchesonis on 2011-04-17
Please forgive my ignorance, but is removing Unity as simple as removing it using the Software Center, and installing Gnome3 the same way?

Also, given the issues with having them both on the same computer, it is wise to uninstall Unity first and then install Gnome3?

---

### Post by grege on 2011-04-17
Unity runs on top of Gnome 2.32 libs, so it will not coexist with Gnome 3. That way will lead to dependency hell. If you select Classic Gnome at the login prompt it is 2.32.

I have Unity and Xubuntu in a parallel install and they seem happy so far.

Xubuntu uses Xfce 2.8 and it is very slick for those who want to ease into Unity slowly or not at all.

We have Kubuntu and Xubuntu, how long before we have Gubuntu?

:)

---

### Post by grege on 2011-04-17
> **timchesonis said:**
> Please forgive my ignorance, but is removing Unity as simple as removing it using the Software Center, and installing Gnome3 the same way?

Also, given the issues with having them both on the same computer, it is wise to uninstall Unity first and then install Gnome3?

It will never be simple. Gnome 3 will not be in Software Center. It will require a PPA to be added to your software sources.

Experimenting on a spare machine might be a sensible move.

Simple instructions, but beware all is experimental at this stage

[http://norman.hooper.name/blog/post/58/ubuntu-natty-narwhal-gnome-3/](http://norman.hooper.name/blog/post/58/ubuntu-natty-narwhal-gnome-3/)

I am just finishing up a Gnome3 install on a disposable setup. Installations was easy now for the testing.

Edit:  Confirming going down this path stops Unity and Classic Gnome, they will no longer start. This would be expected with lib clashes.  Xubuntu loads, seems OK but requires more testing.

I can see myself ending up an Xfce user, but I will play with Unity and Gnome3. Who knows, I might grow to like one or the other.

---

### Post by 3rdalbum on 2011-04-17
> **HeavyAl said:**
> And again as so many others have said prior to this release the buttons for windows being on the top left is a ridiculous 'innovation' that adds nothing useful to the user experience.

The top-left close button has been in Mac OS since 1984.

Top-right window buttons are a relatively recent "innovation", having been introduced in Windows 95 which was released in 1995.

It's really such a minor change. I go between Windows, Ubuntu 11.04 and Ubuntu 9.10 all the time and it doesn't trip me up too much. Is it really that difficult for you to get used to it?

---

### Post by promet on 2011-04-17
> **timchesonis said:**
> Please forgive my ignorance, but is removing Unity as simple as removing it using the Software Center, and installing Gnome3 the same way?

Also, given the issues with having them both on the same computer, it is wise to uninstall Unity first and then install Gnome3?

Well, I have a pretty "Devil May Care" approach to adding and removing packages, unless I'm well aware of what will and will not get broken. As long as I've got decent backups, I'm willing to take the risk. I have read though, but not tested myself (read as "beware"), that removing the ppa:[INDENT][FONT=arial]"You can download the PPA-purge (it's in the Natty repositories) and install it, then use the command above to remove the repositories[/FONT]"
[/INDENT][INDENT]```
sudo ppa-purge ppa:<repository-name>/<subdirectory>
```[/INDENT]this will re-enable Unity and Ubuntu Classic, I've heard...Since I jumped in the deep end of the pool, and the above "solution" seems reasonable, I wouldn't uninstall Unity myself, unless I got some reports that it was the best thing to do. It's early to be second guessing though, so I'm just going to forge ahead.

---

### Post by Supergoo on 2011-04-17
Unity is not ready for primetime. The menus need to be worked on. Unity is clunky, Ubuntu needs at least another release cycle to polish Unity. There is no reason they could not have stayed with the old Gnome for 1 more release cycle. But they are rushing Unity out. I suggest they look around the web,Unity is not popular, they need time to polish this interface,

---

### Post by irv on 2011-04-23
I know the finial release date is only 6 days away, and I am ready for 11.04 but I am not ready for Unity or Gnome 3 yet. I have been playing around with Suse and Fedora and Gnome 3, and both seem to work OK in these distos, but not so in Ubuntu. (The reason is because of the lib for 2.32. I agree that more testing and development is need it on both, and that Ubuntu should have stayed with Gnome 2.32, and then move to Gnome 3 as it matures. I think Unity is not the way to go, I have a new Hard Drive set and ready to go when 11.04 comes out, but I am going to go with the classic gnome until things improve. Call me old fashion but I like gnome 2.32.  

One side note. 11.04 beta did not play well with my wifi card, 10.04 and 10.10 needed to install additional driver to work. Fedora just finds it and sets it up. Why can't Ubuntu do this? I always thought Linux didn't play well with my wifi, but some distors just work but not so with Ubuntu.

Even though Fedora finds my wifi I don't like it. I like Ubuntu better.

---

### Post by ziawiki on 2011-06-03
Some Unity and Gnome3 missing points: no "apps list running" on taskbar, no "clear recent documents".

1.
There is no taskbar showing what apps are opened.
If there are 2/3 apps opened it is easy to browse thru them with ALT+TAB.
But if there are 20+ apps opened it is very unpractical to browse thru them with ALT+TAB.
Xfce in Xubuntu and LXDE in Ubuntu still retain the taskbar.

2.
Opening documents always leaves a trace in the cache.
Both Unity and Gnome3 no longer have any "clear recent documents".
Is there any way to simply clear any opened document trace?
Xfce in Xubuntu has xfce-plugin-places that gives this option.

Unity and Gnome3 are very non user-friendly and non straigth-forward for users coming from Windows.

Unity and Gnome3 are not suitable to work withe many windows opened, cos the big hassle to browse thru open apps.

KDE/Xfce/LXDE are more user-friendly and straigth-forward for users coming from Windows.

Some links where you can see other points of view of people un-happy with Unity:
[http://www.ghacks.net/2011/02/27/the-latest-ubuntu-unity-good-or-bad/](http://www.ghacks.net/2011/02/27/the-latest-ubuntu-unity-good-or-bad/)
[http://www.zdnet.com/blog/open-source/the-new-ubuntu-desktop-unity/8584?pg=2&tag=mantle_skin;content](http://www.zdnet.com/blog/open-source/the-new-ubuntu-desktop-unity/8584?pg=2&tag=mantle_skin;content)
[http://www.pcpro.co.uk/blogs/2011/05/03/ubuntu-unity-the-great-divider/](http://www.pcpro.co.uk/blogs/2011/05/03/ubuntu-unity-the-great-divider/)
[http://arstechnica.com/open-source/reviews/2011/05/riding-the-narwhal-ars-reviews-unity-in-ubuntu-1104.ars](http://arstechnica.com/open-source/reviews/2011/05/riding-the-narwhal-ars-reviews-unity-in-ubuntu-1104.ars) (see "One of the weakest areas of the Unity dock in 11.04 is its poor support for managing applications with multiple windows")
[http://distrowatch.com/weekly.php?issue=20110509#feature](http://distrowatch.com/weekly.php?issue=20110509#feature) (see "lack of customizing options")
[https://communities.bmc.com/communities/blogs/linux/2011/05/24/ubuntu-1104-first-impressions](https://communities.bmc.com/communities/blogs/linux/2011/05/24/ubuntu-1104-first-impressions) (see Paul Kloves comment)

---

### Post by irv on 2011-06-04
> **irv said:**
> I know the finial release date is only 6 days away, and I am ready for 11.04 but I am not ready for Unity or Gnome 3 yet. I have been playing around with Suse and Fedora and Gnome 3, and both seem to work OK in these distos, but not so in Ubuntu. (The reason is because of the lib for 2.32. I agree that more testing and development is need it on both, and that Ubuntu should have stayed with Gnome 2.32, and then move to Gnome 3 as it matures. I think Unity is not the way to go, I have a new Hard Drive set and ready to go when 11.04 comes out, but I am going to go with the classic gnome until things improve. Call me old fashion but I like gnome 2.32.  

One side note. 11.04 beta did not play well with my wifi card, 10.04 and 10.10 needed to install additional driver to work. Fedora just finds it and sets it up. Why can't Ubuntu do this? I always thought Linux didn't play well with my wifi, but some distors just work but not so with Ubuntu.

Even though Fedora finds my wifi I don't like it. I like Ubuntu better.

Above is my old post before the release of 11.04. I would just like to update it after reading the post above.
I gave Ubuntu 11.04 a good try. (about a month). I also installed Gnome 3. (I will say I liked it better then Unity), but really didn't care for either. After all was said and done, I wanted to go back to Gnome 2.32 but I know it is going away now that Gnome 3 is out so I installed XUbuntu with the Xfce DE. I have been only using it less then a week and I am going to stay with Xubuntu 11.04 until the next release and then see if what Ubuntu 11.10 looks like. If they stay with Unity or Gnome 3 I may just go with Xubuntu 11.10.

---

