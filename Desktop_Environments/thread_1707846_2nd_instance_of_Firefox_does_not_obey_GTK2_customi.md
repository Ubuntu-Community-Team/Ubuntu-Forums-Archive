---
title: "2nd instance of Firefox does not obey GTK2 customizations"
date: 2011-03-15
forum: Desktop Environments
---

### Post by cocorocara on 2011-03-15
Hi  On Ubuntu 10.10 I started a 2nd instance of Firefox using the command:
$ firefox -ProfileManager -no-remote &  
  Created a new profile and everything works smoothly except for the  fact that this instance of FF does not obey by GTK2 customizations that I  have placed in ~/.gtkrc-2.0
  Moreover, only **SOME** of the customizations are not  obeyed. For example, the vertical scrollbars are supposed to be on the  left, but they are on the right. The scrollbar arrows are together  (Mac-like) as specified, so is the scrollbar width.
  The first instance obeys all customizations with scrollbars on the left. Any ideas?

---

### Post by Krytarik on 2011-03-15
My experience is that we can be happy that Mozilla's apps "obey" GTK specifications at all in some way, since they are not GTK apps. But it is indeed odd that the second instance doesn't follow specs which the first one does. I have no idea on how to fix this.

---

### Post by Frogs Hair on 2011-03-16
I set up multiple instances of Firefox on the panel each displaying properly when opened.  Firefox uses the GTK theme to draw something similar . I have to ask if you have tried tried other themes with the same result ?

---

### Post by Krytarik on 2011-03-16
> **Frogs Hair said:**
> I set up multiple instances of Firefox on the panel each displaying properly when opened.
Do they all run the *same* Firefox installation (if that matters)? Or do they run FF3 and FF4, for example, like I have?

---

### Post by cocorocara on 2011-03-17
Something very strange is going on. First of all, the problem was solved by syncing both profiles. A simple `rsync -avz <old_profile_dir> <new_profile_dir>` does the trick.

But it still doesn't explain why this was happening. As far as I know, I haven't installed any extensions or themes to tweak Firefox. Moreover I have only one installation 3.6.15 of Firefox. Now for something much more interesting:

Check [this screenshot]([http://freeshells.co.uk/~cocorocara/images/Screenshot_Before.png](http://freeshells.co.uk/~cocorocara/images/Screenshot_Before.png)) of Gmail before syncing the profiles. Notice that the scrollbar is on the right. At the top right, it displays "xxx@gmail.com" and the labs icon, settings, etc. On the top left, the menu is black and underlined.

Now see [this screenshot]([http://freeshells.co.uk/~cocorocara/images/Screenshot_After.png](http://freeshells.co.uk/~cocorocara/images/Screenshot_After.png)) of Gmail after syncing the profiles. Not only is the vertical scrollbar on the left, but more interestingly, the Gmail UI is totally different. On the top right it displays the name "XXX XXX" rather than "xxx@gmail.com", and everything else goes under the "wheel". Clicking on the wheel opens up mail settings, account settings, etc. On the top left, the menu is bigger and bolder blue, with no underlines. Overall font size is 1-2 points larger.

So what is this mystery? Why does the Gmail UI change? Why are the scrollbars on the left?

---

### Post by Frogs Hair on 2011-03-17
> **Krytarik said:**
> Do they all run the *same* Firefox installation (if that matters)? Or do they run FF3 and FF4, for example, like I have?
 
I only use Minefeild and Opera .

---

### Post by Krytarik on 2011-03-17
> **cocorocara said:**
> 
So what is this mystery? Why does the Gmail UI change? Why are the scrollbars on the left?
Thanks for the detailed comparison!

The reason for this might be:
- cookies
- cache
- "/chrome/userChrome.css" in your profile dir
- "/chrome/userContent.css" in your profile dir

Unfortunately we can't track it anymore, unless you backed up the problem profile dir before!?

---

