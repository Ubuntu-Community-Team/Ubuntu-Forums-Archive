---
title: "Openbox related questions"
date: 2008-06-12
forum: Desktop Environments
---

### Post by Totalchaos02 on 2008-06-12
1. Is it possible to remove icons from the Client-List-Combined-Menu (The middle click menu)?

2. Not really an Openbox question but I need help with it anyway. How can I permanently change the color and font of xterm? If I use xterm -bg white -fg black it opens a new terminal with those settings but that is as far as it goes.

Thanks in advance for the help.

---

### Post by urukrama on 2008-06-12
> **Totalchaos02 said:**
> 1. Is it possible to remove icons from the Client-List-Combined-Menu (The middle click menu)?

Not that I know.

> **Totalchaos02 said:**
> 2. Not really an Openbox question but I need help with it anyway. How can I permanently change the color and font of xterm? If I use xterm -bg white -fg black it opens a new terminal with those settings but that is as far as it goes.

You could specify these things in your ~/.Xdefaults file. You would have to add the following to get what you specified:

> xterm*background: white
xterm*foreground: black

See [here]("http://tecumseh.srv.ualberta.ca/hyperdispatch/HyperDispatch2/Xterm.html") for more options.

---

### Post by Totalchaos02 on 2008-06-12
Once again you are a great help urukrama. You're guide pretty much walked me through setting up Openbox last night. Thank you so much for the quick response.

---

### Post by urukrama on 2008-06-12
You're welcome :)

---

