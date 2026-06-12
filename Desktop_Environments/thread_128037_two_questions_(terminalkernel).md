---
title: "two questions (terminal/kernel)"
date: 2006-02-10
forum: Desktop Environments
---

### Post by Ramses de Norre on 2006-02-10
I have two more questions:)

1) When I type the commands "locate", "grep" or "apt-cache search" with an argument in a gnome terminal, I don't get output.. But I do when I'm in a text only mode (ctrl+alt+F1-6). So I'd like to be able to use this commands in the gnome terminal.. In Konsole, both locate and apt-cache search work but grep doesn't.
I don't get an error report of any kind, just a new prompt without any output..

2) I found a lot of info on k7 and 686 kernels, but they're all telling me something else.. I'm running an AMD Athlon 64 3700+ , which kernel should I use? I'm running a 368 now, but guess I can get better?

Thx for helping me out;)

---

### Post by zxee on 2006-02-10
I think that the commands working or not is more a function of the shell that you're in rather than the terminal type, and the way ubuntu sets up the default behavior. Shell types are bash, tsh, and csh. There is a way to alter the shell. Maybe do a search on bash commands?
As to the kernel I have a sempron cpu and recently upgraded to k7. It does boot faster now. I think there may be a k8 kernel but not sure if it's available yet.

---

### Post by nihilocrat on 2006-02-10
[QUOTE=zxee]It does boot faster now.[/QUOTE]

Oh come on, *real* nerds never turn off their computers, so that shouldn't really matter. :rolleyes: 

They keep them on all night nabbing video games/movies/anime/whatever off Bittorrent. That, and so they can get some epenis++; from having long uptimes. Wow, that sounded dirty.

I don't believe there is a horribly significant difference between using a stock 386 kernel and a kernel specific for your x86-based platform. I'm certain it will probably boot up faster and run the tiniest bit faster, but I doubt there will be any significant performance boost.

I also highly doubt your terminals are using anything but bash, because bash is generally the default Linux shell and I see no reason why this would be changed unless you did it yourself. To see just what shells are *possible*, type this in a terminal:
```

cat /etc/shells

```

But yeah, I have no real clue as to why those commands are being spotty for you.

---

