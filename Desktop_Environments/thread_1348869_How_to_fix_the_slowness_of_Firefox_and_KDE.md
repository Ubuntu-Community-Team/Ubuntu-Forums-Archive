---
title: "How to fix the slowness of Firefox and KDE"
date: 2009-12-07
forum: Desktop Environments
---

### Post by chenxiaolong on 2009-12-07
If you had been noticing slowdowns in Firefox on Kubuntu or after installing KDE on Ubuntu, here's how to fix the problem. The problems happens to people who have the **Intel GMA 4500MHD** graphics card. 

1. Uninstall the "snort" package if you have it installed. It uses a lot of CPU.

2. Disable KWin and use Compiz. KWin is very slow on this card. KWin is based on Compiz, so you shouldn't be losing any features. 

3. Close all your programs and open up Konsole (or any terminal) and type in "ps aux"--it lists your processes that are running--and check in the "%CPU" column, for programs that are using a lot of CPU. For me, snort was using 40% of the cpu, so I killed the process (using "killall theprocessnamefrompsaux") and removed it and everything is fast now.

Hope this helps. Please tell me if you want me to clarify.

---

### Post by lovinglinux on 2009-12-07
[Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by chenxiaolong on 2009-12-07
Well, I posted my original post to give information on why Firefox runs slowly on KDE, not Firefox running slow in general. You can add my post to your thread if you want.

---

### Post by lovinglinux on 2009-12-07
> **chenxiaolong said:**
> Well, I posted my original post to give information on why Firefox runs slowly on KDE, not Firefox running slow in general. You can add my post to your thread if you want.

Sorry if I hijacked your thread, but since the title says how to fix Firefox slowness, but the tips does not involve Firefox, I thought the readers could benefit from some Firefox optimizations if they find your thread by the title.

Besides, Firefox does not run slow on KDE (I use it) but specifically on Intel chipset you described, which is a graphics problem, not a Firefox problem.

---

### Post by chenxiaolong on 2009-12-07
No, you didn't hijack my thread. I had poor wording in my original post. I'll change it to make it more clear.

---

### Post by Zorael on 2009-12-08
Unless I'm sorely mistaken, KWin isn't *based* on Compiz.

If you want to get an overview or running processes (and what might be hogging cpu time), you can also hit Ctrl+Esc to open up a slim version of the System Monitor (ksysguard), which works like the windows task manager.

Firefox ended up being so slow and unresponsive that I took the leap to Chromium, myself. Its speed is... undeniable. I miss my extensions, though.

---

### Post by chenxiaolong on 2009-12-08
I got my information from here: [http://www.kde-forum.org/artikel/19304/kwin-and-compiz.html](http://www.kde-forum.org/artikel/19304/kwin-and-compiz.html)

And by the way, the real Google Chrome Beta (from Google), is out today for download.

---

