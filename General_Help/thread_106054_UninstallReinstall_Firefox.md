---
title: "Uninstall/Reinstall Firefox"
date: 2005-12-19
forum: General Help
---

### Post by BobSongs on 2005-12-19
Help!

How can I completely uninstall and re-install Firefox 1.0.7 without hurting or breaking anything?

Okay. I installed Firefox 1.5. Heh. Oh well. So, I wanna go back to 1.0.7 where things worked like they were supposed to, albeit "slower".

So I followed the wiki tutorial and managed to restore, pretty much, 1.0.7. But there are things that are broken in 1.0.7 now. And I'd like to scrub it from my system and re-install it, as close to "from scratch" as possible without it wreaking havoc on the whole system.

Even a link to a post or an external link would be fine.

Thanks.

__________

I need to know what I've got to clear out, how many packages I can safely remove, etc. A clean uninstall.

:)

---

### Post by Ted D. on 2005-12-19
Ditto for me as well. Ted D.

---

### Post by Evil Whisper on 2005-12-19
**I'm not quite sure if it will break anything but you can try:**

```

sudo apt-get remove mozilla-firefox && sudo apt-get install mozilla-firefox

```

Then to delete your profile incase if that is creating a problem from your home directory:
```

rm -rf .mozilla

```

---

### Post by BobSongs on 2005-12-19
I like your sig (Caution: Following My Suggestions May Result In Horrendous Results)

Thanks for the advice. Let's wait and see what else gets posted.

Listen: The entirety of Firefox need not be ripped from the system, right down to all the components required by various other applications.

It would be sufficient to gut all the plugins and customizations so that when it fires up it looks like it did when first run.

I can re-customize it. That'll do just fine.

Thanks.

---

### Post by Evil Whisper on 2005-12-19
If you want to delete all your plugins and stuff just open up your console and make sure your in your home directory and type:

```

rm -rf .mozilla

```

This will remove your profile and all your extensions.

If you want to remove the plugins like java, flash, etc.  Then open up your terminal and type this:

```

sudo nautilus /opt/firefox/plugins/

```

Delete all the plugins in this folder except libnullplugin.so

Open up firefox and you should have a new profile and you can recustomize it.


Hope This Helps,
- Evil Whisper

PS: Thanks for the compliment on my signature :p

---

### Post by BobSongs on 2005-12-19
Alrighty. I'll give that a try. If there's a horrendous result... I was warned. ;)

---

### Post by Evil Whisper on 2005-12-19
Ok :-) let me know if it works.  If not I'll dig around and see if I can come up with anything else.

---

### Post by BobSongs on 2005-12-19
Okie dokie.

Scalpel in hand, I approach with fear and trepidation. :|

;)

---

### Post by BobSongs on 2005-12-19
*wipes hands*

Well; the operation's done. Looks like it was a success.

Odd though; first site I went to was Homestarruner.com to see if Flash had remained behind. Sure enough h*r displayed in Flash. Now that could be because of the various methods I've used to install Flash system-wide.

Thanks to all for the assistance.

---

### Post by Evil Whisper on 2005-12-19
Your welcome.

I'm glad it worked out. :-)

If you need anymore help with anything just give a shout and I'll do my best to help.

- Evil Whisper

---

### Post by b05q on 2007-02-04
someone ought consider putting this in the beginner  guide.  i'm sure i'm not the only person who's fired up firefox, went straight to the extensions page to load up on goodies, only to find it won't start.  and ubuntu won't let you uninstall it through normal methods (what is up with that????) .

anyways, thanks for helping the newbs.

---

