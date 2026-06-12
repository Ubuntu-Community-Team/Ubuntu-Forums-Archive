---
title: "Gaim Xmms Current song plugin"
date: 2005-12-06
forum: Desktop Environments
---

### Post by vishnumrao on 2005-12-06
I am trying to install the xmmscurrsong pluging downloaded from sourceforge, Link: [http://sourceforge.net/projects/xmmscurrong/](http://sourceforge.net/projects/xmmscurrong/)


"Tarred" the file and the readme file says: 

"just copy the plug  (xmmscurrsong in ~/.gaim/plugins.
after, start gaim , preferences-->tools; check xmmscurrsong

if you wanna compil the plug you need src of gaim (0.80 or more)
put  file.c in gaim-0.80/plugin.
../configure
make xmmscurrsong.so LDFLAGS=-lxmms
cp *.so ~/.gaim/plugins"

Now I cannot find a /.gaim directory. There are some gaim plugins in /usr/lib/gaim. 
Took a chance and copied the .so plugin to this directory. Restarted gaim but nothing yet in the preferences about xmms yet. 

If I put the plugin in the wrong directory, which is the right one? 

Please advice me on what I could have done wrong.
Thanking you in advance,
Vishnu Rao.

---

### Post by vishnumrao on 2005-12-06
Update

Browsing through the other preferences, plugins tab tells me all the plugins are in /usr/lib/gaim/. which where I have copied my plugin too. 

But beats me why its not showing the xmmscurrsong in the list. 

BTW in the terminal window  the new plugin is in green while the rest are in black letters. Any idea why?

---

### Post by cilynx on 2005-12-06
your .gaim should be in your home directory:

rcw@tranq:~$ ls .gaim/
accels  accounts.xml  blist.xml  icons  prefs.xml  smileys

I'm not sure if there should be a "plugins" directory under the ".gaim" directory or not as I don't use plugins.

In ls world, green means executable

---

### Post by vishnumrao on 2005-12-07
My .gaim directory has same contents as above. And no plugins directory either. I tried copying the pluging to the /home/myusernam/.gaim directory. Still the gaim preferences does not give me the xmmscurrsong option. 

Any help appreciated.
Thanks,
Vishnu Rao

---

### Post by kwaanens on 2006-02-26
I found [this]("http://zulutango.org:82/journal/entry/202") which might do the thing you're after. The i686-version did the trick for me. At least putting in %s in a conversation prints the current song playing.

- Ketil

---

### Post by vbmaster on 2006-02-26
[QUOTE=kwaanens]I found [this]("http://http://zulutango.org:82/journal/entry/202") which might do the thing you're after. The i686-version did the trick for me. At least putting in %s in a conversation prints the current song playing.

- Ketil[/QUOTE]

wtf? the microsoft site?!

---

### Post by kwaanens on 2006-02-26
[QUOTE=vbmaster]wtf? the microsoft site?![/QUOTE]

What the h***?!? How did that happen?!?
I fixed the link now.
Apparently, putting in [http://http://and.so.on](http://http://and.so.on) sent you (and me) to MS instead.  Weird...

- Ketil

---

### Post by TheIdiotThatIsMe on 2006-02-26
[QUOTE=vbmaster]wtf? the microsoft site?![/QUOTE]

The link seems to have accidentally have two http:// so just copy and paste the link and take out the second http:// (or just click [here]("http://zulutango.org:82/journal/entry/202") ;) )

---

### Post by jms830 on 2006-03-26
hey is there somewhere else we can get what that link leads to, because it isnt working anymore

---

