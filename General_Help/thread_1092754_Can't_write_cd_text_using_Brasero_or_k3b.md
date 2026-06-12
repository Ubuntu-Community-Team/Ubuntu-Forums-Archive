---
title: "Can't write cd text using Brasero or k3b"
date: 2009-03-10
forum: General Help
---

### Post by mb_webguy on 2009-03-10
I recently tried to burn some of my mp3s to an audio CD so my sister-in-law could listen to them in her car (which doesn't play mp3 cds).  The problem is that neither k3b or Brasero will write the CD text.  I didn't have this problem in Hardy, and this is probably the first time I've tried burning an audio CD in Intrepid, since my car stereo will play mp3 discs, and I don't need discs any other time.

Since the problem exists in both Brasero and k3b, the problem has to be with a common library that handles cd text.  I don't suppose anyone knows what library this might be, or else knows a fix or workaround for this problem?

---

### Post by Yellow Pasque on 2009-03-10
Are you sure the player you're using is capable of reading CD text format?

---

### Post by yther on 2009-03-10
I don't see any CD-text libraries mentioned [on k3b's requirement's page]("http://k3b.plainblack.com/requirements"), but further investigation shows that it is handled by **cdrdao**, "with drives that support it."

So it seems that not all burners can write CD-Text.  Are you certain that yours can?  (I've tried it myself, and never got an error about it, but no device I've put my audio CDs in actually displays the text, so I have no idea if it really works.)  I just checked the burner on this laptop, but all it says is "CD-Text:  auto" which doesn't really tell me anything.

---

