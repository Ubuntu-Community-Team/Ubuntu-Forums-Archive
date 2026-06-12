---
title: "Can't login with kdm"
date: 2005-12-29
forum: General Help
---

### Post by EnGee on 2005-12-29
Hi there,
i installed Kubuntu-desktop in Ubuntu by using apt-get install, everything seemed fine then some X configuration asked me i must choose either gdm or kdm, so i chose kdm, then logged off and logged in kde, changed the resolution of the monitor and then font size in general, then i restart. This is now the problem, can't login through kdm, the login box keep appearing again, and if i choose consule, i can login but there is no any command recognized! (sudo, ls, ..etc), so how can i fix things? how can i change the manager from kdm to gdm? 
Thanks in advance

---

### Post by angrykeyboarder on 2005-12-29
[quote=EnGee]Hi there,
i installed Kubuntu-desktop in Ubuntu by using apt-get install, everything seemed fine then some X configuration asked me i must choose either gdm or kdm, so i chose kdm, then logged off and logged in kde, changed the resolution of the monitor and then font size in general, then i restart. This is now the problem, can't login through kdm, the login box keep appearing again, and if i choose consule, i can login but there is no any command recognized! (sudo, ls, ..etc), so how can i fix things? how can i change the manager from kdm to gdm? 
Thanks in advance[/quote] 
So to "fix things" you just want to go back to GDM?

I'm having pretty much the same problem, but I don't want to use GDM. I want KDM to work.

But as how to swtich back just:

```
sudo dpkg-reconfigure gdm
```

---

### Post by EnGee on 2005-12-29
[QUOTE=angrykeyboarder]So to "fix things" you just want to go back to GDM?

I'm having pretty much the same problem, but I don't want to use GDM. I want KDM to work.

But as how to swtich back just:

```
sudo dpkg-reconfigure gdm
```[/QUOTE]

Yes as you said sudo dpkg-reconfigure kdm was the solution, BUT i needed to boot in recovery mode! because this command wasn't recognize in consule mode while booting normally!, anyway i will check now if kde woking, i had strange errors in gnome though, if kde is still not 'ready' for me as it was in suse, mandrake ..etc, then i will stay with gnome.

---

