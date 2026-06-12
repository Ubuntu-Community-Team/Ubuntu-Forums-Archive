---
title: "Xubuntu slowly with games / laptop battery."
date: 2012-10-11
forum: Desktop Environments
---

### Post by Portaro on 2012-10-11
Hello for all, i use a Xubuntu remaster on my 2 pcs - one desktop and one laptop.

In past i also use an xubuntu 12.04 and the problem i following describe dont happen.

When i substitue the xubuntu 12.04 with an XUbuntu remaster called Voyager i have two problems, on my desktop pc the games are slowly, like assault-cube or warzone2100.
And in my laptop i have the problem of slow games and when i have the pc in work with battery mode the desktop Xfce is very slow some applys need 1 minute to open or more.

In past when i use Xubuntu (not a remaster) i dont experiment this problem, but now with voyager i have the problem related.

I try some solutions like remove Xserver-video ati and reinstall, edit xorg, add xorg-edgers, install opengl etc, but nothing work, i my 2 pcs the problem is the same. I think maybe this can caused by any tool of the remaster i use.

IN my desktop pc the graphic driver is an Ati 9250 PRO so dont exist a proprietary driver to the pc and i need use the open drivers, but in my laptop the graphic driver have a support drivers of ati and the problem is the same.

Can anyone give to me an idea?

---

### Post by LewisTM on 2012-10-11
This is a support forum for Ubuntu and official derivatives. Since you clearly state that Xubuntu works well for you, then it's clearly a problem with the customizations made in Voyager. It would be difficult for most of us to find the cause of you problem. Perhaps you would have more luck if you wrote in a Voyager-specific forum or support mailing list. I hope you speak French...

If nothing helps, you might think of simply installing Xubuntu and adding AWN, Conky and other Voyager tweaks in a stepwise fashion so you can look out for signs of slowdown, if any.

Cheers!

---

### Post by Portaro on 2012-10-11
:p thanks.

---

### Post by jefsview on 2012-10-11
Avant Window manager uses a lot of resources, and is heavy on compositing. try disabling that. Also Synapse uses zeitgesit, which is running in the background.

I liked a lot about Voyager, but it used nearly twice as much resources as I was confortable with (I use 3D art programs via Wine), so I saved my Conky configs and switched back to plain Xubuntu. When I ran Voyager, I had removed AWN and Synapse and other things, that used resources. So I cherry-picked what I liked most about it, and put them on Xubuntu 12.04 with Xfce 4.10 and everything runs smoothly.

If you like Synapse, Xfce 4.10 has a new, better Application finder that works very similiar, but just isn't as pretty ;)

-- Jeff

> **Portaro said:**
> Hello for all, i use a Xubuntu remaster on my 2 pcs - one desktop and one laptop.

In past i also use an xubuntu 12.04 and the problem i following describe dont happen.

When i substitue the xubuntu 12.04 with an XUbuntu remaster called Voyager i have two problems, on my desktop pc the games are slowly, like assault-cube or warzone2100.
And in my laptop i have the problem of slow games and when i have the pc in work with battery mode the desktop Xfce is very slow some applys need 1 minute to open or more.

In past when i use Xubuntu (not a remaster) i dont experiment this problem, but now with voyager i have the problem related.

I try some solutions like remove Xserver-video ati and reinstall, edit xorg, add xorg-edgers, install opengl etc, but nothing work, i my 2 pcs the problem is the same. I think maybe this can caused by any tool of the remaster i use.

IN my desktop pc the graphic driver is an Ati 9250 PRO so dont exist a proprietary driver to the pc and i need use the open drivers, but in my laptop the graphic driver have a support drivers of ati and the problem is the same.

Can anyone give to me an idea?

---

### Post by Portaro on 2012-10-11
Thanks Jeff stopped zeitgeist on task manager and it increase the games performance, thanks for your advice.

Thanks for your help.

---

