---
title: "Sound Driver?"
date: 2009-02-05
forum: General Help
---

### Post by Josshill on 2009-02-05
Where can I get a Driver for my Sound card its a "Realtek AC97". Also, If my skype is saying "Problem with Playback audio" That is my Sound card right?

Joss

---

### Post by 73ckn797 on 2009-02-05
You might find info here:
[http://www.realtek.com.tw/faqs/faqsView.aspx?Langid=1&PFid=6&Level=3](http://www.realtek.com.tw/faqs/faqsView.aspx?Langid=1&PFid=6&Level=3)

Go to Applications/Accessories/Terminal and enter the code:

```
sudo lshw
```look for *-multimedia section (near top) to see if it is recognized by system.

A shorter list would be entering code:
```
 aplay -l
```

Also look here:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Josshill on 2009-02-05
Alright, My sound is playing no problem. It would take sound input, My skype says no Audio playback. Any idea?

---

### Post by 73ckn797 on 2009-02-05
I do not use Skype so I cannot help you there..

---

