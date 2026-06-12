---
title: "Install Mono and MonoDevelop"
date: 2005-12-26
forum: General Help
---

### Post by nami on 2005-12-26
Hi

I would like to try out Mono and the MonoDevelop IDE, but have no idea how to install them!  I don't even know if it uses glade, glade 2, WxWindows, or something else for the user interface design!

Here are the main links, but am not sure what other stuff I need with this or how easy it is to install these on Linux Ubunto 5.10.

[Mono FrameWork]("http://www.mono-project.com/Main_Page") and [MonoDevelop IDE]("http://www.monodevelop.com/Main_Page")

Please help

nami

---

### Post by pmjdebruijn on 2005-12-26
Hi,

To be honest, you could have  **easily**  figured that out by now...


First, Mono uses GTK# for widgetry...

Second Ubuntu package have dependancies which automatically install everything (for example) MonoDevelop needs...

Third, I can recommend glade-gnome for easy interface design, make sure you read up on the GNOME HIG.


So just install monodevelop through Synaptic, and everything you need will automatically be installed along with it... You'll have to add Glade manually because it's not strictly needed.

Regards,
Pascal de Bruijn

---

### Post by nami on 2005-12-26
Hi

Thanks for the reply.  I tried that and the installation went smoothly.  However, when I try to build a project it gives me the following errors:

[IMG]http://img276.imageshack.us/img276/5170/screenshot07xe.png[/IMG]

[IMG]http://img276.imageshack.us/img276/5170/screenshot07xe.png[/IMG]

[IMG]http://img499.imageshack.us/img499/887/screenshot27kx.png[/IMG]

[IMG]http://img402.imageshack.us/img402/4038/screenshot35vm.png[/IMG]

[IMG]http://img499.imageshack.us/img499/4825/screenshot46gk.png[/IMG]

Click to enlarge:
[[IMG]http://img499.imageshack.us/img499/6135/screenshot58qh.th.png[/IMG]](http://img499.imageshack.us/img499/5493/screenshot57xe.png)

Any ideas why this could be.  The project was just a blank window, nothing more nothing less!

nami

---

