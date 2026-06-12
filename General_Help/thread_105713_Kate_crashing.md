---
title: "Kate crashing"
date: 2005-12-19
forum: General Help
---

### Post by Kadin2048 on 2005-12-19
I just installed ubuntu earlier this week and changed over to Kubuntu via the kubuntu-desktop package.

Everything seemed fine, but suddenly Kate stopped working and now crashes when I try to open it. If I try to open a text file from the GUI, I get the "progress" cursor for about 30 seconds and a new pane at the bottom of the screen, which disappears after a while with no output.

If I try to run kate from a terminal window, I get
"kate: ERROR: Communication problem with kate, it probably crashed."

I tried running systrace on it, and couldn't really find anything in the resulting file that meant much to me, but I will attach it. The last few lines are:
```
stat64("/usr/share/kubuntu-default-settings/kde-profile/default/share/config/kdebugrc", 0xbff63f48) = -1 ENOENT (No such file or directory)
open("/etc/kde3/kdebugrc", O_RDONLY|O_LARGEFILE) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=2116, ...}) = 0
fstat64(4, {st_mode=S_IFREG|0644, st_size=2116, ...}) = 0
mmap2(NULL, 2116, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7f50000
fstat64(4, {st_mode=S_IFREG|0644, st_size=2116, ...}) = 0
rt_sigaction(SIGBUS, {0xb751fb8c, [], SA_ONESHOT}, {SIG_DFL}, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
fstat64(4, {st_mode=S_IFREG|0644, st_size=2116, ...}) = 0
munmap(0xb7f50000, 2116)                = 0
rt_sigaction(SIGBUS, {SIG_DFL}, NULL, 8) = 0
close(4)                                = 0
write(2, "kate: ERROR: Communication probl"..., 67) = 67
close(3)                                = 0
exit_group(255)                         = ?
```

The error is repeatable, I've tried it several times and the systrace result is essentially the same every time.

I've also tried uninstalling kate, doing apt-get clean, then reinstalling it, to no avail.

Not really sure what to try at this point. I've put just enough time into this system now that I'd really hate to have to reinstall everything, but I need kate working. Suggestions?

---

### Post by Brando569 on 2005-12-19
ive had that too, the thing where you click something once and you get the busy cursor and it doesnt do anything. sounds like a problem in KDE it seems like its in every version. maybe its hardware specific? the way i rememdy is it i just click the app again and it launches. even though it is annoying...

---

### Post by Kadin2048 on 2005-12-19
Tried just clicking on it again, but no dice. If I try to open it again while it's thinking about opening it, I just get two instances of it trying to open, which fail one after the other after the same amount of time on each. (So if I try to open kate once, then wait 2 s and try again, I get two new panes at the bottom of the screen which last ~30 s and the first one goes away 2 s before the second.) It's definitely trying something and then just timing out after a set amount when it doesn't work.

I can't understand how it could be hardware specific since Kate did work right after I installed kubuntu, and the only thing I've done since then is install the nvidia drivers package and the boinc computing client.

My hardware just for reference though, is a HP xw5000 workstation (so it's a 3.2GHz P4) with an NVidia Quadro4 NVS 200 graphics card. It's also got some cheapo Wifi card in there that's using the ndiswrapper drivers, but I think kate was still working after I installed that.

---

### Post by GoldBuggie on 2005-12-19
> ive had that too, the thing where you click something once and you get the busy cursor and it doesnt do anything. sounds like a problem in KDE it seems like its in every version. maybe its hardware specific? the way i rememdy is it i just click the app again and it launches. even though it is annoying...i had that alot before but with 3.5 I've never seen it. Or has anyone else seen that problem in 3.5?

---

### Post by lucidite on 2006-03-04
Hey,

I've just installed Kubuntu (had Ubuntu before) and I have the same problem.

Any way of fixing this?

---

### Post by Kadin2048 on 2006-03-23
Mine seems to have mysteriously fixed itself.

I've encountered a lot of these really bizarre transient problems, and frankly it makes me very nervous. The only thing I like LESS than a problem that begins for no reason is a problem that goes away for no reason -- because now I never know when it's going to happen again.

Needless to say, I'm not using my Ubuntu system in anything approaching a production or even a 'primary home desktop' environment, so these sort of quirks are acceptable ... but it still doesn't give me a good feeling.

Good luck .... sorry I can't be of more assistance.

---

### Post by Barrakketh on 2006-03-23
I had a similar problem after doing a big upgrade (namely, to Dapper).  You can try this after logging in under recovery mode or by choosing a console login.

```
sudo rm -rf /var/tmp/kdecache-*
sudo rm -rf /tmp/kde*
```

---

### Post by SteveF on 2006-03-30
I had a similar problem and the only way I could fix it was to install kedit.  Not sure why that worked.

Steve

---

