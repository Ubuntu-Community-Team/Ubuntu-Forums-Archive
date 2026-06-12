---
title: "gimp-svg"
date: 2006-09-10
forum: Desktop Environments
---

### Post by paulmerchant on 2006-09-10
The package for The Gimp's svg plugin has been broken for quite a while. This is what I get when I apt-get for it:

[indent][COLOR="Navy"]The following packages have unmet dependencies:
  gimp-svg: Depends: gimp (= 2.2.11-1ubuntu3) but 2.2.11-1ubuntu3.1 is to be installed
E: Broken packages[/COLOR][/indent]

Two questions. I'm a bit new to Ubuntu. What is the best way to report this? Secondly, does anyone know how to get SVG support back into The Gimp until this is resolved? I've tried Googling for DEB files or binaries of the plugin and looked all over in the files on Gimp.org.

---

### Post by MetalMusicAddict on 2006-09-10
Weird because I just installed this on 2 new machines. Are you using Dapper? Are you using other repos that might have GIMP packages in them?

---

### Post by paulmerchant on 2006-09-10
I have had Universe and Backports installed. Maybe I should try uninstalling The Gimp and then reinstalling it with the svg plug using just the standard repositories. I'll report back if that works.

I've seen a few other people on the boards who haven't been able to install the SVG plug and no answers as to what to do so I thought it was just broken.

---

### Post by paulmerchant on 2006-09-10
> **MetalMusicAddict said:**
> Weird because I just installed this on 2 new machines. Are you using Dapper? Are you using other repos that might have GIMP packages in them?

Thanks, MetalMusicAddict, for pointing me in the right direction.

Yes, I'm on Dapper. I had tried turning off all the other repositories and then installing the svg plug, but that didn't work. After reading your post I decided to turn off everything but the official repositories, uninstall The Gimp (which breaks ubuntu-desktop). Then I reinstalled The Gimp (and ubuntu-desktop) and the gimp-svg package worked.

Problem solved and I've got integration between Inkscape and The Gimp again with the gimp-svg plug. I've been missing that.

---

