---
title: "Sugar XO Desktop Environment"
date: 2009-03-13
forum: Desktop Environments
---

### Post by afrodeity on 2009-03-13
I'm a fan of the Sugar XO desktop environment which has been abandoned somewhat by the OLPC project who are focusing on hardware. It was originally bundled with Fedora but has now been ported to ubuntu and is available using:

```
 sudo apt-get install sugar sugar-activities sugar-emulator
```

The reason why I'm a fan, aside from the beautifully abstract and visually interesting desk is from an evolutionary perspective. I believe it is pedogologically correct to have a system in which you can introduce programmes to the desk, and then put them away, preferably under lock and key. I don't always have enough computer power to operate every bit of the modern desktop which often becomes cluttered. Why must I keep everything in memory somewhere. While procesess can be started and stopped, it is Sugar which offers this solution in a visual way which one might associate with supercomputing. So as you scale up, you can leave more in system memory, then when you need, you can put the application away in a user-friendly manner.

Then there is the fact that you are not expected to remember anything. Your work or desk can be part of an ongoing log in which you can always look back at the various instances of the desk. I would love to have Sugar develop to the point at which you have multiple undoes of the desktop. At least this is what seems to be the metanarrative suggested by the Sugar project
[B]
In the future all computers will be able to do this. [/B]

Again, I like the possibility of infinite virtualisation offered by locking down x spaces in what UNIX freaks refer to as jails. This should be standard on any desktop. The ability to hack away at a part of the system without affecting or compromising the rest. The ability to visually understand the many layers of Ubuntu with Sugar desktop, because, Ubuntu has all of this power which is not being used simply because we are still looking at the OS (and computer) from an old-fashioned bureau or *portmanteau* point of view. A place to keep your pens and calculators, gimzos and gadgets but not the kind of ubiquitous environment in which you can edit video, mashup audio and whiteboard without compromising speed or power, which is what the Sugar desktop would offer us if it was developed as an addition to the Ubuntu Free Desktop like KDE, XFCE and GNOME.

Unfortunately, Sugar on ubuntu is in danger of dying, simply because not enough education has been done on the long-term goals of the Sugar project. Should Ubuntu have a powerful sugar session, and what would happen if this Sugar session took over the look and feel of Ubuntu, would we be willing to sacrifice our Gnome/KDE/XFCE identities? Will Sugar end-up becoming too Ubuntu-like?

I love Gnome, its my friend, but I also like Sugar and the two are about the best desktops next to KDE that I have seen in the world of Linux. Sugar offers us a brand-new environment in which many of the applications available in KDE for instance may take on new form. I have already suggested sugar as a vehicle for modifications and as a place to produce wonderful works of artifice. I would love to see a decent sugar audio playa that interacted with other sugar user's. We are rapidly approaching the point where all this will become a possibility as the network takes on new forms. The sugar desktop is a portal to a new networked reality in which the WWW is merely one facet, not the end goal. Applications that work together in new ways - this is what I foresee in the near future, environments that are rock-solid because of Ubuntu, with all the speed that we can bring without compromising serendipity, creativity, conscious exploration.

Any thoughts on this subject would be appreciated.:)

Here are some Sugar on Ubuntu links:
 [Sugarlabs.org Community-Distributions-Ubuntu]("http://wiki.sugarlabs.org/go/Community/Distributions/Ubuntu")

[wiki.laptop.org Sugar on Ubuntu]("http://wiki.laptop.org/go/Sugar_on_Ubuntu")

---

### Post by athaki on 2009-03-13
Never used Sugar. Thought it was an intersting concept.

---

### Post by SLA_leandrin on 2009-05-17
Mmmm I've installed it in Kubuntu Jaunty, but I just can't log in to Sugar. 

The first time it asked me for "name" and "coulour" but when I clicked next nothing happened and just sent me back to the login screen.

After that, now just the log in screen and nothing more. Any toughts?

---

### Post by afrodeity on 2009-05-18
> **SLA_leandrin said:**
> Mmmm I've installed it in Kubuntu Jaunty, but I just can't log in to Sugar. 

The first time it asked me for "name" and "coulour" but when I clicked next nothing happened and just sent me back to the login screen.

After that, now just the log in screen and nothing more. Any toughts?

Silly me, I knew there was something I had forgotten to mention, and now I can't seem to find the correct instruction. You have to edit your .desktop file. Will see if I can find the page where I saw this, before getting all caught up in Sugarising things, since I also need to reinstall sugar after a recent upgrade.

---

### Post by afrodeity on 2009-05-18
The following is from [http://www.nubae.com/sugar-on-ltsp-ubuntu-intrepid-ibex]("http://www.nubae.com/sugar-on-ltsp-ubuntu-intrepid-ibex")

Then change the default session to sugar like this:

```
 sudo nano /home/$username/.xsession 
```

(where $username is the user for whom you want sugar to be the default shell.)

And add the following to the .xsession file:

```
export SUGAR_LOGGER_LEVEL=debug
export GABBLE_DEBUG=all
export GABBLE_LOGFILE=/home/$user/.sugar/default/logs/telepathy-gabble.log
export PRESENCESERVICE_DEBUG=1
export LM_DEBUG=net
exec ck-launch-session dbus-launch --exit-with-session sugar-shell
```

A quick explanation of the file is in order. The export lines are actually for debugging, and aren't needed if you don't intend to look at the log files. Remember $user should be the user home folder. The ck-launch-session is for making sugar exit properly when exiting from the menu. The --exit-with-session is for making sure there are no lingering sessions on ctrl-alt-backspace, currently the only way to exit, as ck-launch-session doesn't seem to work.

Finally, make sure you have your server hostname in place of olpc.collabora.co.uk:

```
sudo sed -ie "s/olpc.collabora.co.uk/hostname/" /home/username/.sugar/default/config
```

I hacked the above and played with something .desktop and got a nice sugar session running, but without an exit option. Would appreciate any work-arounds for pulseaudio which is now preventing me from starting the session. Will post my debug file.

---

### Post by afrodeity on 2009-05-19
I'm going to contact the sound guys with this one:

```
 /etc/gdm/Xsession: Beginning session setup...
setting IM thorugh im-switch for locale = en_ZA.
start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default
***PULSEAUDIO: unable to connect: Connection refused
** (sugar-shell:13118): CRITICAL **.
_wrap-gstmixer-list-tracks: assertion 'GST_IS_MIXER (self->obj)' failed 
```

---

### Post by afrodeity on 2009-07-03
```
sudo rm -rf ~/.sugar
```

then

```
 sudo apt-get remove sugar sugar-activities
```

reinstall

```
 sudo apt-get install sugar sugar-activities
```

Works. Great sugar session with sugar terminal, journal, pippy, and a bunch of activities, but missing the following:

sound - no sound and no sound activity.

an xo package installer

network setttings for a DSL modem - Sugar expects a wireless connection, of a particular type related to the XO laptop. There is a settings control panel with a server input, but nothing more. 

Anybody know how to workaround these issues?

---

### Post by oliwek on 2009-10-03
sugar (0.84) had no problem to find my wifi hardware on my ubuntu desktop pc, then connected to my router out of the box and I saw other sugar users connected (through jabber.sugarlabs.org, the ejabber server set as default in the network settings)

I have also tested [trisquel]("http://trisquel.info/en/trisquel-sugar") (an ubuntu based distro 100% free software) + sugar 0.86 installed in virtualbox, and I had to set a virtual ethernet network in virtualbox (to find my ubuntu host wifi connection), so ***sugar doesn't have to rely on wifi***, I guess...

[IMG]http://trisquel.info/files/sugar.png[/IMG]

---

