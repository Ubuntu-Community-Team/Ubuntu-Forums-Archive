---
title: "Locking icons into Docky"
date: 2012-07-08
forum: Desktop Environments
---

### Post by timbo59 on 2012-07-08
I'm trying to come to terms with 12.4 after upgrading from 10.4, and part of the issue has been making frequently used programs readily available via the desktop. Aside from Unity, which I find a little tedious, I also wanted to add Docky to the Desktop where I can store my most commonly used apps. I've never used it before on Ubuntu (I use Rocketdock on my Windows-based PC) and have found some kind of glitch to its usage. The only way I can figure to add icons to Docky is to put the necessary icons on to the Desktop, then drag them into Docky. Once done, I then delete them from the Desktop. Unfortunately this method isn't working, because I discovered this morning that all the icons I added yesterday have disappeared from Docky. After a little experimenting this morning I realized that the only way I can make the icons stay in Docky is to keep the original icons on the Desktop itself, which is obviously a little redundant. Is there some step I'm missing, or an alternative way I'm supposed to put the icons in Docky that locks them in place? 

Thanks.

---

### Post by irv on 2012-07-08
First, I do not use Docky. Let me ask you, are you using Ubuntu 12.04 with the Unity desktop? if so, then you have the Dash to the left side of the screen. When you open an app it will appear in the dash. If you right mouse click on it you can lock or unlock it from the dash. You can also move it up and down. This allows you to put the apps you use the most to the top of the dash.
I find this much more useful then using Docky.
I know this didn't answer your question, but I thought I would just pass this information on to you.

---

### Post by timbo59 on 2012-07-08
No, as I mentioned in my first post, I do have the latest version of Ubuntu on board, as well as Unity loader.  

The point was that I wanted to add Docky to the Desktop for more usability and flexibility. Because of the ability to reduce the size of the icons considerably in Docky across the bottom of the screen compared to Unity, one can keep a considerable amount of programs readily available via a single mouse click, as against having Unity loaded to the gills and having to scroll up and down to get to a program icon. Horses for courses - a horizontal docking application allows considerably more scope for icon storage than a vertical equivalent such as Unity, especially on a wide screen. That's why I find it a little odd that the developers of Unity didn't allow for the mechanism to be moved to different locations on the desktop.

 I actually intend using both, but with the more common apps along the bottom in Docky.

---

### Post by irv on 2012-07-08
I thought about using Docky because of the icon size in the Dash until I saw I could make them smaller in the CompizConfig setting. Just go to the Unity setting and make them smaller.
[ATTACH]220903[/ATTACH]

---

### Post by timbo59 on 2012-07-08
Already done to the most it can be minimized - which again gets back to the original issue about wanting to use Docky. I can get twice as many icons on my screen across the bottom as I would with Unity Launcher in its vertical mode. 

Getting back to the original post, can someone with experience of Docky give me any kind of insight on why I keep losing the stored icons every time I shut down the machine? I've played around with it further today and still can't figure out whether it's an issue with the program or some kind of bug with 12.04?

---

### Post by irv on 2012-07-08
I think it has something to do with the gconf-editor which can be installed via the Software center. I found this is ask Ubuntu.
[http://askubuntu.com/questions/143733/how-to-remove-docky-anchor-icon-in-12-04]("http://askubuntu.com/questions/143733/how-to-remove-docky-anchor-icon-in-12-04")
I don't know if this will help, remember I don't use Docky.
I have been waiting for someone who uses docky to jump in here, but in till they do I thought I would post this.

---

### Post by timbo59 on 2012-07-09
Problem solved - very simple in the end. I was taking a Windows approach, and only figured it out when I kept noticing how programs kept popping up in Docky every time I opened them. Right clicking to copy and paste icons on to the Desktop out of Dash had not worked earlier, and based on that experience I never thought to right click the icons when I had them in Docky, else I would have seen what was necessary.

So in the end I managed to figure it out for myself, even though it took going backwards and forwards with it during the day to get there.

---

### Post by irv on 2012-07-09
Glad you figure out how to get it to work. Sorry I couldn't have been more help, but without using Docky, it didn't help. I wished someone else would have jumped in, but glad it is solved now.

---

