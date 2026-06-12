---
title: "Migrate from Dapper/XGL/Compiz to Edgy/XGL/Beryl"
date: 2006-10-31
forum: Desktop Environments
---

### Post by msandersen on 2006-10-31
I just upgraded to Edgy, all went fine. I have XGL and Compiz set up as a separate session in GDM. Looking around, it seems my best bet is to move to Beryl, though I'll stay with XGL for my nVidia card. I would like to retain it as a separate session since it's development software that might break, and doesn't work so well with OpenGL apps.
I've found some guides, namely [this one]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL") on the Beryl site and [this one]("https://help.ubuntu.com/community/CompositeManager/Xgl") for Dapper which shows how to set up an XGL session. There's a few other links to use AIGLX with x.org 7.1 etc, but I think XGL/Beryl is perhaps the best to try for now.
I'm not particularly happy about Compiz forking, and would perfer the more "official". but not much is said of using Compiz, and some say Beryl is better for now.

So: What needs to be removed or otherwise done? I imagine Compiz has to be removed first. Are there any dependencies that need to be removed also? The names have changed in Beryl, like the window decorator.
The CompositeManager instructions I used for Dapper mentions *compiz-start* and has a [toggle script]("https://help.ubuntu.com/community/CompositeManager/InstallingCompiz#head-7495b494dff525c8a78b8275a42aa425536c32be") that mentions *compiz* and *cgwd*. Any update to this script posted somewhere, or is there a better way?

In short; What needs to be done to migrate XGL/Compiz to Edgy using XGL/Beryl? What needs removing first? 
Thanks.

---

