---
title: "Can I remove evolution  -common?"
date: 2009-03-17
forum: Desktop Environments
---

### Post by Sealbhach on 2009-03-17
I prefer not to use Evolution or any of the built in calendar functionality or any of that. I always remove Evolution, but if I try to remove evolution-data-server and evolution-common it threatens to remove just about everything.

Is it OK to remove evolution-data-server & evolution-common without completely crippling Ubuntu?


.

---

### Post by ellgor on 2009-03-17
Hi,

If you have already removed Evolution then you can remove the rest of the packages (just tried it to make sure) I used synaptic at one package per go, just in case, and it even took out Ekiga (which has been a bummer to get rid of) Hardy-dont know about Jaunty.

Regards, Ellgor.

---

### Post by Sealbhach on 2009-03-17
OK great, thanks. I'll give it a go.;)


.

---

### Post by ugm6hr on 2009-03-17
Actually, I'd be very wary of removing those packages.

Check to ensure that gnome-panel doesn't require them as dependencies first.

---

### Post by Sealbhach on 2009-03-17
> **ugm6hr said:**
> Actually, I'd be very wary of removing those packages.

Check to ensure that gnome-panel doesn't require them as dependencies first.

Yup, it removed the panel so I had to reinstall the panel again which also reinstalled the evolution-data-server.


.

---

### Post by ugm6hr on 2009-03-17
> **Sealbhach said:**
> Yup, it removed the panel so I had to reinstall the panel again which also reinstalled the evolution-data-server.

The problem is that the panel uses Evolution for its calendar plugin.

Evolution is just a little too integrated into Gnome.

---

### Post by GraysonPeddie on 2009-03-18
Yeah. I was also trying to remove anything to keep it light-weight down to just using GNome for my home server (used VNC to access my server in my network when it comes to VirtualBox).

It'd be better if GNome could develop a package that could integrate to/disintegrate from the Gnome panel.

---

### Post by Sealbhach on 2009-03-18
> **ugm6hr said:**
> 
Evolution is just a little too integrated into Gnome.

Yup, it seems to be the Internet Explorer of the Ubuntu world.


.

---

### Post by youknowwhat4q on 2009-03-20
> **Sealbhach said:**
> Yup, it seems to be the Internet Explorer of the Ubuntu world.


.


hahaha

Awesome.


Pretty much the best you can do is remove the actual program, or just take it out of your main menu; out of sight out of mind.

---

