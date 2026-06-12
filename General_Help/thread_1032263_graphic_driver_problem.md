---
title: "graphic driver problem"
date: 2009-01-06
forum: General Help
---

### Post by Elya on 2009-01-06
Dear All,

I have a graphic driver problem. I try to run Visual Molecular Dynamics (VMD) but I can not do it in graphical mode.
When I tried glxinfo
I have got the following.

name of display: :0.0
X Error of failed request: BadRequest (invalid request code or no such operation)
Major opcode of failed request: 143 (GLX)
Minor opcode of failed request: 19 (X_GLXQueryServerString)
Serial number of failed request: 10
Current serial number in output stream: 10

Can somebody advise me what to do?
Thanks in advance.

---

### Post by redilyn on 2009-01-06
What video card are you using?

You can check using this command from a terminal
```

lspci | grep VGA

```

---

### Post by Elya on 2009-01-07
Result of this command is 

lspci | grep VGA


00:02.0 VGA compatible controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)

---

