---
title: "How to redirect the command line output to the clipboard"
date: 2009-02-02
forum: General Help
---

### Post by Kejing on 2009-02-02
Sometimes, I would like to post some topics on the forum, and the contents of the topics come from the output the command line output. 

Usually, I would run the command, and copy the output to the clipboard and then paste it here. I think it is a efficient less way to do the job and I am looking for if Bash has such kind of the feature.

---

### Post by matthew.ball on 2009-02-02
Edit: Upon further investigation, xclip might be what you are after!
I found this link: [http://elcasey.wordpress.com/2008/02/12/xclip-use-the-clipboard-from-the-command-line/](http://elcasey.wordpress.com/2008/02/12/xclip-use-the-clipboard-from-the-command-line/) which to me, sounds like what you're after.

---

### Post by adamlau on 2009-02-02
If you happen to use Thunar/Nautilus, here is the appropriate action using xclip:

```

echo -n %F | xclip -selection "clipboard"
```

---

### Post by Kejing on 2009-02-02
It seems to be quite strange. According to the man page, I followed the example in the man page:

uptime | xclip

the redirected content went to the clipboard, if I want to use it in the X application, I just simply press the middle button of the mouse.

While I tried your solution
uptime | xclip -selection "clipboard"

when I right clicked the mouse, the "paste" function in the pop-up menu is useless. 

puzzled, anyway, it solved my problem, thanks a lot

---

