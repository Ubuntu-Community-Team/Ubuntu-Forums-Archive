---
title: "How should I use texhash command to update natbib?"
date: 2012-02-28
forum: Education &amp; Science
---

### Post by arroy_0209 on 2012-02-28
I had problem in updating natbib, though the process should be simple. I have doubt exactly how the command texhash is to be used. Can anybody please tell?

I downloaded the latest natbib.zip, unzipped in a new directory, extracted the natbib.sty and bibentry.sty. Then I used 

```
sudo texhash /usr/share 
```

and then ```
source ~./bashrc
``` (This method is given in some previous post)
 After this when I try to latex some file, I get the latex warning which says that the latest natbib.sty version is "unavailable" to the compiler. I have also checked that the extracted natbib.sty file is newer than the older version of natbib available. Why is this happening? I have also used ```
sudo texhash
``` and ```
sudo /usr/share....../natbib
``` i.e., giving the entire path for the actual location of natbib.sty file. All attempts failed. What am I doing wrong?

---

