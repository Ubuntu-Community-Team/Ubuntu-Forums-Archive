---
title: "Beryl/Compiz Fusion both work on Feisty, but Gutsy (live cd) effects don't?"
date: 2007-10-18
forum: Desktop Effects &amp; Customization
---

### Post by rainwalker on 2007-10-18
I'm currently running Feisty on an Inspiron 8600,  ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] video card.
I'm not using the restricted ATI accelerated graphics driver and Beryl/Compiz Fusion work fine. However, I decided to try the Gutsy live cd (official release) to see if the effects worked, but for some reason they don't. 
I don't think it's a driver problem, because I'm using the same driver (I think?).
This makes me wary of upgrading to Gutsy...any suggestions?

---

### Post by mrvertigo on 2007-10-19
odd, you sure your running the open mesa driver in feisty? mmm odd lemme look into it

---

### Post by rainwalker on 2007-10-19
How do I check what driver I'm using?

---

### Post by lazyart on 2007-10-19
type compiz at the terminal and post the output.

---

### Post by superyounan1 on 2007-10-19
if you at some point installed the fglrx drivers (official ati restricted drivers), you'll have to reinstall them because gutsy is using a new kernel

---

### Post by mrvertigo on 2007-10-19
Thanks superyounan1 i forgot that for a second :P

---

### Post by Amaranth on 2007-10-19
I believe your card is one of the ones we've blacklisted due to driver problems.

---

### Post by rainwalker on 2007-10-20
Augh, for some reason I didn't get any notification there were replies.

> type compiz at the terminal and post the output.
Output:> There is already the metacity win manager running, you should use the --replace option to override it
compiz --replace gives:> A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
inotify_add_watch: No such file or directory
GConf backend: There is an unsupported value at path /apps/compiz/plugins/water/allscreens/options/toggle_wiper_key. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
/usr/bin/compiz.real (snow) - Info: Loaded Texture snowflake.png
GConf backend: There is an unsupported value at path /apps/compiz/plugins/cube/allscreens/options/unfold_key. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/cube/allscreens/options/next_slide_key. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/cube/allscreens/options/prev_slide_key. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

---

### Post by rainwalker on 2007-10-20
[quoteif you at some point installed the fglrx drivers (official ati restricted drivers), you'll have to reinstall them because gutsy is using a new kernel[/quote]
If you're talking about the "ATI Accelerated Graphics Driver" in the restricted drivers manager, I tried that a while back but Beryl/Compiz Fusion didn't work with it, so I don't use it. However, I think I do remember going into some X configuration utility (it was acccessed via the command line) but I don't remember what it was called, and I think I chose a certain driver to use (not a restricted one, though).

---

### Post by rainwalker on 2007-10-20
> **Amaranth said:**
> I believe your card is one of the ones we've blacklisted due to driver problems.
What does that mean? That it won't run from the live cd, but it will if I upgrade?

---

### Post by soxs on 2007-10-20
This means that you should have a look at this page, which tells you what to do.. BUT! BE AWARE that your graphics accelerator was blacklisted for good reasons... [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

---

### Post by rainwalker on 2007-10-20
> **soxs said:**
> This means that you should have a look at this page, which tells you what to do.. BUT! BE AWARE that your graphics accelerator was blacklisted for good reasons... [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)
I'm sorry, I don't understand what that page is saying
Does that mean if I upgrade to Gutsy, I'll have no desktop effects? I already have Beryl and Compiz Fusion on Feisty with no problems (except that CF crashes a lot, and Beryl never does), so shouldn't the effects in Gutsy work too?

---

### Post by soxs on 2007-10-23
3d desktop effects are disabled for your PC , as the driver is not stable enough (sacrifying stability for 3d effects is really dumb). So, the named page tells you how to force compiz(-fusion) to ignore the blackblist which stops your system from getting 3d desktop stuff (for good reason, stability).
I hope you understand now. If you've got some spare money(well, money is never spare ^^), I suggest you to buy an nVidea card, at least for the moment..

---

### Post by rainwalker on 2007-10-23
Well I upgraded, and now things look weird (and I'm not even using the effects.
My theme colors are all mixed up and even lacking in some places, and my refresh rate is PAINFULLY slow. 
What happened? I know I'm using the same driver I've used since Edgy, maybe even Dapper

---

