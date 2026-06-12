---
title: "Display Host Name on Desktop"
date: 2009-06-25
forum: General Help
---

### Post by spherics on 2009-06-25
I have a Ubuntu 9.04 desktop installation and I'd like to display the host name on the top menu bar or panel.

The reason being I have three U9.04 desktops running through a KVM switch connected to a single monitor, and it would save a lot of confusion if I could see the host name of the machine I'm connected to.

I have had a look at the Add To Panel options and couldn't see anything that will help there.

Can anyone suggest a neat way to get the host name onto the menu bar ?

Thanks; Spherics.

---

### Post by Cheule on 2009-06-25
I have a similar situation - although just the two desktops. I just simply use gimp to overlay the hostname onto the desktop background. Obviously not really helpful if you change your backgrounds a lot I suppose.

---

### Post by Divider on 2009-06-25
I would have to agree, using a labeled background would be the simplest solution.

---

### Post by dcstar on 2009-06-25
> **spherics said:**
> I have a Ubuntu 9.04 desktop installation and I'd like to display the host name on the top menu bar or panel.

The reason being I have three U9.04 desktops running through a KVM switch connected to a single monitor, and it would save a lot of confusion if I could see the host name of the machine I'm connected to.

I have had a look at the Add To Panel options and couldn't see anything that will help there.

Can anyone suggest a neat way to get the host name onto the menu bar ?

Thanks; Spherics.

Not in the menu bar, but I run **gkrellm** and it has that info (along with lots of other useful stuff)

---

### Post by t4ggs on 2009-06-25
maybe u can use conky and configure it to show only the hostname

---

### Post by spherics on 2009-06-25
Thanks guys

I have considered labeling the background, but of course there will often be a window open over it obscuring the host name.  Hence putting it on the top menu bar seems a better option.

The closest approach I have got so far is to put an application launcher icon on the menu bar.  When you hover over the icon it shows the command string and comment which can be the host name, however this is still quite poor.

What I really want is the ability to put a short text string on the menu bar, but I don't know how to go about writing a module that would display a text string like that.

I wasn't aware of conky I will give that a look.

Any other suggestions, or guidance on writing a text string module, appreciated. 

Regards; Spherics.

---

### Post by hwttdz on 2009-06-25
So you could add a launcher for the panel to execute some command, say terminal, but then change the icon to a custom icon, and create an icon in gimp that's just the host name.

---

### Post by VastOne on 2009-06-25
> **dcstar said:**
> Not in the menu bar, but I run **gkrellm** and it has that info (along with lots of other useful stuff)

+1 for Gkrellm

Very easy to setup and a host of monitoring tools and options

---

### Post by dcstar on 2009-06-26
> **spherics said:**
> 
.......
What I really want is the ability to put a short text string on the menu bar, but I don't know how to go about writing a module that would display a text string like that.

I wasn't aware of conky I will give that a look.

Any other suggestions, or guidance on writing a text string module, appreciated......

libsensors-applet-plugin-dev
Create plugins for the 'sensors-applet' package

---

