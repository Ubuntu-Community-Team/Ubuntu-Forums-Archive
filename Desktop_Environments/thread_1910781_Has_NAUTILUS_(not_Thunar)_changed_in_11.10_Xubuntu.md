---
title: "Has NAUTILUS (not Thunar) changed in 11.10 Xubuntu?"
date: 2012-01-17
forum: Desktop Environments
---

### Post by WinRiddance on 2012-01-17
Hi everyone.
I recently came came back home to "buntuland after trying out Mint for awhile in order to get away from Unity & Gnome3. So now I'm using Xubuntu and I'm very very pleased with it since the XFCE is super configurable, just the way I had it looking with Ubuntu before Unity came crashing in ... :o.

Anyway, having used Nautilus ever since Ubuntu 9.04 this was one of the first apps that I installed. My previous Ubuntu version was 10.10 and my previous Mint version was 11.04 ... with Nautilus looking and behaving as I was used to it in the past. However, Nautilus looks different in Xubuntu 11.10 and it really bugs me that there's "stuff" in the left pane that I don't want to look at. I've attached some screenshots ...

Basically I want to be able to configure Nautilus with all of my bookmarks in a way that I won't ever have to scroll up or down. Right now I can't do that because of all of the new extra junk that shows up in the left pane. The Mint image (left) is how I want Nautilus to look in Xubuntu. Any ideas? I'd really appreciate it. Thanks.

---

### Post by Frogs Hair on 2012-01-17
Nautilus changed with the introduction of Gnome 3 , but the places pane on the left that is crossed out in the screen shot was included in Gnome 2  . You still have Gnome 3 , but you are using XFCE on top of it in place of Unity . The only settings are found under Edit > Preferences .

---

### Post by Krytarik on 2012-01-17
Adding to what *Frogs Hair* just said; the content of the "Places" sidebar is exactly the same, the only differences are that those items are now differently sorted, and the newly built groups have headers above them, that's all. ;-)

And no, afaik you can't remove the headers, or hide certain items.

Regards.

---

### Post by WinRiddance on 2012-01-18
Thanks, but now I'm even more confused ... sorry. I didn't downgrade Mint or Ubuntu. I reformatted my system partition and then installed Xubuntu 11.10 with default XFCE from scratch. So are you saying that when I installed Nautilus it was the updated version of Nautilus that would be found in Ubuntu 11.10 with Gnome3 ... ???

I went to this site and downloaded the last non Gnome3 version of Nautilus:
[http://www.icewalkers.com/Linux/Software/511910/Nautilus.html](http://www.icewalkers.com/Linux/Software/511910/Nautilus.html)

It's a tar.gz file. Can you help me figure out how to install the contents of that tar.gz file in lieu of the Gnome3 Nautilus that I have now? This is not an option for me, I really need to use Nautilus the way I've been using it for the past few years. I use it daily, at least a dozen times per day, and that's how I'd like to continue using Nautilus. Thank you for any assistance that you might be able to provide.

---

### Post by mcduck on 2012-01-18
> **Frogs Hair said:**
> Nautilus changed with the introduction of Gnome 3 , but the places pane on the left that is crossed out in the screen shot was included in Gnome 2  . You still have Gnome 3 , but you are using XFCE on top of it in place of Unity . The only settings are found under Edit > Preferences .

...actually XFCE is not a shell you could run on top of another desktop environment, like Unity or Gnome Shell. It most certainly is a desktop environment of it's own.

But you are right about the left panel changes happening already before the Gnome Project moved to Gnome 3.

What comes to Nautilus looking different, there were some changes to the user interface, but the most striking difference based on the screenshots is that WinRiddance isn't using a GTK3-compatible theme, which leaves Nautilus using the default theme instead. Switching to a theme that supports both GTK3 and the old GTK2 is a good idea now that many programs have already moved to GTK3, while some are still stuck with the old GTK2.

---

### Post by WinRiddance on 2012-01-20
Okay, eventually I switched to the **pcmanfn** file manager because that one only has the two blocks on the left as opposed to three. Single click, open as administrator, bookmarks, bookmark moving/renaming are all available, thus making pcmanfn a great alternative.

In the end I went back to Nautilus though because Nautilus has an extension plugin that I really use a lot, which is not available with any of the other file managers. By having bookmarks to the folders that I use on a daily basis ... which don't include Music, Video, Documents, and other default ones .... I'm able to have Nautilus work for me. I just find it irritating that places and system folders have been combined since I'm sure that I'm not the only one who uses some of those folders on an external disk to which I should be able to make my own bookmarks (for documents, music, videos, etc.). Ah well ....
The evolution of Linux ... :D

---

