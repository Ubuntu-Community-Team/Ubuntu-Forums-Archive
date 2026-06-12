---
title: "[SOLVED] my compiz went ubuntu"
date: 2007-08-26
forum: Desktop Effects &amp; Customization
---

### Post by Chymera on 2007-08-26
i have been using compiz for over 3 weeks now, but half an hour ago, after I restarted my computer my compiz fusion  got ubuntued... 
when typing compiz --replace i got something complaining about my inotify_add_watch directory... so i looked it up on the forum and followed some smart-@ss instructions that seem to have gotten me into more trouble...
you can find that godsend of a thread [here]("http://ubuntuforums.org/showthread.php?t=477536&highlight=inotify_add_watch").
I typed ```
gconftool-2 --recursive-unset /apps/compiz
``` into a terminal, just like one of the guys said he did, and voila, i get an even bigger error message, which this time reads: 
> GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Initially i thought this may be a step forward, so i navigated to those keys, and guess what?
they were within the parameters that the instructions said they should be... ok, i noted them all down, and deleted the entries just like the thread linked above said.... of course i just got zeros so i had to look them all up again and copy the original values....

Bottom line: any ideas how to get compiz back?

---

### Post by hyperair on 2007-08-26
First remove /apps/compiz in GConf.
```

rm -r ~/.gconf/apps/compiz

```

Then restart your system:
```

sudo shutdown -r now

```

Then log into a terminal (Ctrl+Alt+F1), reinstall Compiz Fusion
```

sudo apt-get autoremove compiz* --purge
sudo apt-get install compiz compizconfig-settings-manager libcompizconfig-backend-gconf compiz-fusion*

```

Then go back to your GDM screen: Ctrl+Alt+F7

Then log in.

Then start Compiz Fusion:
```

compiz --replace

```

And voila. It should work.

---

### Post by Chymera on 2007-08-26
I get this again

> GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

---

### Post by Chymera on 2007-08-27
There seems to be an issue with the packages from trevinos repo lately....

ok, so if anyone is experiencing the same problem here's what you do: 
1 - bang your had at it and waste 10 hours in the process
2 - uninstall it altogether, change to amaranths repo, download compiz-fusion from there
3 - and hope trevino is gonna fix his repo soon because i dont see the point of compiz without 3dwindows :-P

---

### Post by hyperair on 2007-08-28
No point of Compiz without 3d windows?! You gotta be kidding. What about the other plugins? Scale for instance? I can't live without that one.

---

### Post by Chymera on 2007-10-14
It was meant to be humorous...

---

### Post by hyperair on 2007-10-14
Lol, ok ok fine.

---

### Post by frederik.nnaji on 2008-01-15
3d windows...
when compiz-fusion dev team portrays it's incredible software, they use the 3dwindows plugin for those pretty demo screenshots... 

but once u have CF installed on your box, it refuses to show up with these pretty 3dwindows:
that's whack

because it's very disappointing. Since the official screenshots promise such a great effect, you will naturally
expect it to work out of the box. But it doesn't and that shakes the mood.

3dwindows actually gives compiz-fusion the "edge", since it does something unseen on any other platform..

holla

---

