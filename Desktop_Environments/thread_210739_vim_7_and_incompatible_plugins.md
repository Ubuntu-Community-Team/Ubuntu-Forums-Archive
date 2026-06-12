---
title: "vim 7 and incompatible plugins"
date: 2006-07-07
forum: Desktop Environments
---

### Post by mygravity on 2006-07-07
Hi there,

Am using Ubuntu 6.06 with vim 6 and the showmarks plugin.

After upgrading to vim 7 today I experienced some errors from the
showmarks plugin. On opening a PHP file the following error is displayed at the bottom of the screen:

Error detected while processing function <SNR>12_ShowMarks:
line    6:
E10: \ should be followed by /, ? or &

If I type /mo to display marks on The following message is displayed:
:exe 'norm \sm'.nr2char(getchar())<bar>call <sid>ShowMarks()<CR>o

Likewise if I type /mt to toggle ShowMarks on or off the following
message is shown:
:exe 'norm \sm'.nr2char(getchar())<bar>call <sid>ShowMarks()<CR>t

Anyone know how to fix this? I assume that the showmarks.vim file needs to be upgraded for vim 7 but I'm not sure how to do this.

Thanks

Andrew

---

