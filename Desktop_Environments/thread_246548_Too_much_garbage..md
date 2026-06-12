---
title: "Too much garbage."
date: 2006-08-29
forum: Desktop Environments
---

### Post by brucevangeorge on 2006-08-29
My Ubuntu system comes with alot of apps that I do not even use. These apps also have libraries and other crap. Is there a way to figure out what is not used?

For example: I do not need the video codecs. I remove the Movie Player... but it leaves the codec libraries on the system. How do I identify which packages aren't needed?

---

### Post by Sam on 2006-08-29
Install **deborphan**.

Or in Synaptic, menu Settings / Filters / New, name: Orphaned, option to tick: Orphaned. Then in the "Custom" view (bottom left), you'll have the orphaned packages list.

---

### Post by croak77 on 2006-08-29
Install deborphan then run it from a terminal. It will show you all unneeded packages.

---

### Post by Uncle Spellbinder on 2006-08-29
> **croak77 said:**
> Install deborphan then run it from a terminal. It will show you all unneeded packages.

Are they automatically deleted? I see the unneeded packages, but that's it. Were they deleted or is there another step to be taken?

---

### Post by Sam on 2006-08-29
> **Uncle Spellbinder said:**
> Are they automatically deleted? I see the unneeded packages, but that's it. Were they deleted or is there another step to be taken?

No this is just a list. Delete them with apt-get.

Use the Synaptic trick above if you're not familiar with the shell.

---

### Post by brucevangeorge on 2006-08-29
Yup the app worked a little too good. It also deleted my gnome. Needed to reinstall.

---

### Post by lapsey on 2006-08-29
Deborphan did not do that. Both apt-get and synaptic tell you what they are removing.

---

### Post by lepre on 2006-08-29
> **lapsey said:**
> Deborphan did not do that. Both apt-get and synaptic tell you what they are removing.

should i know every single package? ](*,)

---

### Post by andb on 2006-08-29
Try gtkorphan. Graphical interface, you can romove directly. Very esy to use. I dont think it installs into the menu though, so call it from the command line or create a menu icon. Should be invoked with gksudo.

---

### Post by Uncle Spellbinder on 2006-08-30
> **andb said:**
> Try gtkorphan. Graphical interface, you can romove directly. Very esy to use. I dont think it installs into the menu though, so call it from the command line or create a menu icon. Should be invoked with gksudo.

Thanks! It installed fine for me. Shows up in "administration" as *Remove Orphaned Packages*.

[IMG]http://img.photobucket.com/albums/v694/unclespellbinder/Blog/GTK_Orphan.png[/IMG]

---

