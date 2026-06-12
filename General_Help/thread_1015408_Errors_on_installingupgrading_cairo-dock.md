---
title: "Errors on installing/upgrading cairo-dock"
date: 2008-12-18
forum: General Help
---

### Post by Roger Allott on 2008-12-18
I had cairo-dock installed previously from the normal intrepid repositories, but then I [read]("https://help.ubuntu.com/community/CairoDock") that that version was old and no longer maintained. It was recommended instead to set up the special cairo-dock repository as a package source, where the newer stable version is stored and maintained.

So I did that and indeed, version 1.6.3.1 was now available with a flag to upgrade. So I clicked and selected 'Upgrade' and then hit 'Apply' as per normal. By default, it added the new version of cairo-dock-plugins as the dependency package.

After the download though, the install seems to have hit a problem. I got the error message:
```
E: /var/cache/apt/archives/cairo-dock_1.6.3.1_all.deb: trying to overwrite `/usr/share/cairo-dock/icon-mouse.png', which is also in package cairo-dock-data
```

I looked at the details part of the report but couldn't copy the text for some reason, so I took a screenshot that might assist someone in working out what's wrong.

[IMG]http://62.233.105.201/screenshots/Screenshot-Changes-applied.png[/IMG]

Anyone got any ideas as to how I should try to rectify my problem?

---

### Post by fabounet on 2008-12-19
you should remove completely (purge) your system from cairo-dock, then re-install it from its repository.

---

### Post by Roger Allott on 2008-12-19
> **fabounet said:**
> you should remove completely (purge) your system from cairo-dock, then re-install it from its repository.

Ah, thanks. I thought that might be what I'd have to do. I've just done this via Synaptic and the reinstallation gave no errors.

Now off to find out what it is, how to set it up and how to configure it.

---

