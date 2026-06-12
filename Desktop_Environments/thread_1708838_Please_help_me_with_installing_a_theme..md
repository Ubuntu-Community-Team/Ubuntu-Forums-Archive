---
title: "Please help me with installing a theme."
date: 2011-03-17
forum: Desktop Environments
---

### Post by kheaven on 2011-03-17
I downloaded this theme:
[http://gnome-look.org/content/show.php/Conky_Ken?content=134705](http://gnome-look.org/content/show.php/Conky_Ken?content=134705)

And I have gone through the installation for it, but the weather part of it isn't working.

Can someone help me with this?

Thanks in advance.

---

### Post by stinkeye on 2011-03-17
> I downloaded this theme:
[http://gnome-look.org/content/show.p...content=134705](http://gnome-look.org/content/show.p...content=134705)
If you followed the instructions in that download it uses ppa:conkyhardcore which has changed.
The first part of the link I posted shows how to remove the old conky ppa and add the new one.

Also make sure you have installed the **conky-all** package and not the **conky** package.

Install [**_[COLOR="DarkRed"]conkyforecast[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=869328").

---

### Post by kheaven on 2011-03-17
> **stinkeye said:**
> If you followed the instructions in that download it uses ppa:conkyhardcore which has changed.
The first part of the link I posted shows how to remove the old conky ppa and add the new one.

Also make sure you have installed the **conky-all** package and not the **conky** package.

Install [**_[COLOR="DarkRed"]conkyforecast[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=869328").

This is the response when I try to delete the old ppa files:
"rm: cannot remove `/etc/apt/sources.list.d/m-buck*': No such file or directory"

Please help.

---

### Post by king EZi on 2011-03-18
> **kheaven said:**
> This is the response when I try to delete the old ppa files:
"rm: cannot remove `/etc/apt/sources.list.d/m-buck*': No such file or directory"

Please help.

You can try and install Y PPA Manager and use that to remove the repository entry [http://www.webupd8.org/2010/11/y-ppa-manager-easily-search-add-remove.html]("http://www.webupd8.org/2010/11/y-ppa-manager-easily-search-add-remove.html")

---

### Post by stinkeye on 2011-03-18
> This is the response when I try to delete the old ppa files:
"rm: cannot remove `/etc/apt/sources.list.d/m-buck*': No such file or directory"

Please help.

That just means you didn't have that ppa. That's normal.
It checks for 2 old ppas. You only had the conkyhardcore ppa.

...and for it all to work make sure you have followed instruction #8.
> 8. Copy the folders "bin", "Conky" and the file "conkyForecast.config" into your
   Home directory ('/home/[NAME]/').
	- **[COLOR="Red"]Make the folders and the data you just copied, invisible.[/COLOR]** (IMPORTANT!)
			-> Rename it and write a point before the name (.).

Eg In your home folder you should have...
the folders **.bin** and **.Conky**  ([COLOR="DimGray"]ctrl+h to show hidden files[/COLOR])
and
the file **.conkyForecast.config** with your **weather.com** LICENCE_KEY and PARTNER_ID

---

