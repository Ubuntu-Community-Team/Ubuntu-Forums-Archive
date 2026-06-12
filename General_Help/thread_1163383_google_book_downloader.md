---
title: "google book downloader"
date: 2009-05-18
forum: General Help
---

### Post by sn0m on 2009-05-18
Hi guys, is there a google book downloader or a program that would download google books and convert them to pdf for you in linux.
Regards
Sokol

---

### Post by curley_sue on 2010-02-01
have you tried the firefox solution?

[http://sharad-pathology.blogspot.com/2009/03/how-to-download-google-books.html](http://sharad-pathology.blogspot.com/2009/03/how-to-download-google-books.html)

works for me
(need to read through the "traps"; eg 
"In flashGot options select "browser built in" option"
)

---

### Post by sofasurfer on 2010-03-06
I found the script but don't know what I should do with it. Can you help? I think I need to save it to /usr? Is there anything else I need to do with it?

---

### Post by cornflayke on 2011-01-08
Hey, 

I don't know if this is to late for you sn0m, but if it helps:
After downloading everything to ~/Desktop/tmp with FlashGot I transformed every png named books(#number) with pngtopdf like:
for e in {1..#number); do pngtopdf books\($e\) book-$e.pdf; done
and after that merged all the pds together with pdfsam.

Best regards 
- cornflayke

---

