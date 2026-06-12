---
title: "startup script help"
date: 2009-05-19
forum: General Help
---

### Post by taget on 2009-05-19
Hello, i have MPD starting at boot which works fine but the playlist it is suppose to stream errors out with curl saying it a cannot resolve the address, im assuming this is happening becuase the network is not ready. how do i make it start after the network is there ? i have google lots and cant seem to find the right answer, any help will be greatly appreciated.

tag

---

### Post by paradigm2 on 2009-05-19
> **taget said:**
> Hello, i have MPD starting at boot which works fine but the playlist it is suppose to stream errors out with curl saying it a cannot resolve the address, im assuming this is happening becuase the network is not ready. how do i make it start after the network is there ? i have google lots and cant seem to find the right answer, any help will be greatly appreciated.

tag

I a pinch I just use a "sleep 15" command within a script.  This tells it to wait 15 seconds before starting it.  But I'm sure there are more elegant ways such as checking with ping or checking the status of the networking device.

---

### Post by taget on 2009-05-19
Thanks for the reply Paradigm, when you use the sleep command does it allow the rest of the boot to continue ? also what is the syntax ?

sleep 15
command i want to run ?

thanks again

tag

---

