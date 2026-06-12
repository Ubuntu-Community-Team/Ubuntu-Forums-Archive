---
title: "Mark Shuttleworth's solution stuffs up my window close button"
date: 2010-08-13
forum: Desktop Environments
---

### Post by beesblaas on 2010-08-13
I read Mark Shuttleworth’s response to left side button criticisms here:
[http://www.ubuntugeek.com/mark-shuttleworths-response-to-left-side-button-criticisms.html](http://www.ubuntugeek.com/mark-shuttleworths-response-to-left-side-button-criticisms.html)

and his "solution" to fix it was this:
gconftool-2 --set /apps/metacity/general/button_layout --type string “menu:minimize,maximize,close”

So I did that, and it moved the buttons to the right, but now there is no "close" button,
on any window that I open, anywhere. I have to do File > Close.

I then read another solution to the left side button issue, so I checked Metacity, and my settings are correct, i.e. “menu:minimize,maximize,close”
I logged out, logged back in, no change. 

I'm using Ubuntu 10.04.
As a matter of interest, on the same PC another user changed the buttons to the right successfully on his account (I don't know how), but my problem happened when I tried the above fix on my user account.

Any suggestions please? (Please explain in simple terms)

---

### Post by stinkeye on 2010-08-13
Repeat without quotation marks.
```
gconftool-2 --set /apps/metacity/general/button_layout --type string menu:minimize,maximize,close
```

---

### Post by wojox on 2010-08-13
Scroll down to [Minimize, Maximize and Close button placement.]("http://ubuntuforums.org/showthread.php?t=1469475")

---

### Post by beesblaas on 2010-08-13
Thank you Stinkeye !!!!!!!!!!

It now works! All my buttons are on the right of the window.

Quick, easy. So the quotes in the original "solution" were the problem. They should fix the webpage where they give the solution. People like me are not smart enought to figure things out when it does not work- we expect the solution to work exactly as given.
Anyway, I am very happy now.

---

