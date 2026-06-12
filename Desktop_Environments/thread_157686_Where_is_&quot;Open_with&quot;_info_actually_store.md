---
title: "Where is &quot;Open with&quot; info actually stored?"
date: 2006-04-09
forum: Desktop Environments
---

### Post by abovett on 2006-04-09
I have a problem with the way one of the "Open with" options for a particular file type, so I am trying to find where the user-specific configuration for this is really stored, so I can have a go at hacking it manually. 

I imagine there is a table or tables which associates files (either by mime type, magic number or file name extension) with applications somewhere  in gconf or in one of the hidden dot directories I guess, but so far I've been unable to find it. Can anyone help? 

I'm not looking for instructions on how to set up an "Open with" application in gnome, by the way - I know that. I want to go "under the hood" to the actual files that control this an see how it works to see if I can fix the way the parameters are being passed to the program in question.

Thanks

Andy B

---

