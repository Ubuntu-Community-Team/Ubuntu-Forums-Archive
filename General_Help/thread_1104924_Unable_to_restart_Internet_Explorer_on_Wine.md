---
title: "Unable to restart Internet Explorer on Wine"
date: 2009-03-24
forum: General Help
---

### Post by Vpc on 2009-03-24
I installed IE 6.0 (newer versions of IE do not work as well on Wine) with ies4linux on Ubuntu Desktop. After closing IE6, I am unable to restart it after calling IE via command line or by clicking on the desktop icon, without restarting my computer. When I run ps -a I can see IExplorer.exe running but no browser appears. The same with IE 5.5. Is there something I have to configure?

I also have difficulty with the "Favorites" menu in IE under Wine. I can only bookmark urls by creating them in the default "Links" folder they provide. Otherwise, the Favorite does not appear in the drop-down menu. Nor does it appear if I create another folder or rename the Links folder. 

I am using IE to access a website with features that only work in IE.

---

### Post by Denis on 2009-03-24
At the moment I'm also using ies4linux (to check website compatibility). It works for me, but it does have some serious problems. When I quit IE the process continues to run, together with the wine server. It even starts to grow in memory use quickly. 

I think you'll have to shut down IE and wine completely before you can restart it. 

One thing that works for me most of the times is to open ie6 from the terminal, close IE6 when finished and end the terminal process with Ctrl-C. If this doesn't work, check your processes and end or kill "IEXPLORE.EXE" **and** wineserver. Try to restart the program after this.

This clearly isn't an ideal solution. But I hope it helps you, so you don't have to restart your computer every time.

---

### Post by Scubdup on 2009-03-24
Could you use Firefox with one of the IE page viewer addons? I think I use IE Tab.

---

