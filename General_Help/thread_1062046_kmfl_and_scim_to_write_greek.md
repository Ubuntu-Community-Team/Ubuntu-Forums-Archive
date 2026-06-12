---
title: "kmfl and scim to write greek"
date: 2009-02-06
forum: General Help
---

### Post by Eres on 2009-02-06
Hi.
I use Xubuntu Intrepid. I need to write in Greek Polytonic and I found the kmfl ([Keyboard Mapping for Linux]("http://sourceforge.net/projects/kmfl")) project, which provides a scim-engine to use various keyboards with scim. I read [this]("http://www.tedcarnahan.com/2007/11/09/koine-greek-in-ubuntu-gutsy-gibbon") howto, but it doesn't work with Intrepid, because the repository [FONT="Courier New"]http://packages.sil.org/ubuntu[/FONT] not longer contains the package [FONT="Courier New"]scim-kmfl-imengine[/FONT]. I didn't nowhere find this package.
Can you help me?
(I'm sorry for my bad english... :D)

---

### Post by simosx on 2009-02-13
> **Eres said:**
> Hi.
I use Xubuntu Intrepid. I need to write in Greek Polytonic and I found the kmfl ([Keyboard Mapping for Linux]("http://sourceforge.net/projects/kmfl")) project, which provides a scim-engine to use various keyboards with scim. I read [this]("http://www.tedcarnahan.com/2007/11/09/koine-greek-in-ubuntu-gutsy-gibbon") howto, but it doesn't work with Intrepid, because the repository [FONT="Courier New"]http://packages.sil.org/ubuntu[/FONT] not longer contains the package [FONT="Courier New"]scim-kmfl-imengine[/FONT]. I didn't nowhere find this package.
Can you help me?
(I'm sorry for my bad english... :D)

Using SCIM and KMFL to write Greek/Greek Polytonic is currently somewhat complicated. What you can do instead is use the standard Greek Polytonic layout that is provided by the X server.

See [http://simos.info/blog/archives/763](http://simos.info/blog/archives/763)

I do not know if Xubuntu has a GUI tool for setting the layout. 
You may want to use 'setxkbmap', as in

setxkbmap -layout en,gr -variant ",polytonic" -option "grp:shift_toggle"

---

