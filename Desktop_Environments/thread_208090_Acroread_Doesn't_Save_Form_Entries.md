---
title: "Acroread Doesn't Save Form Entries"
date: 2006-07-03
forum: Desktop Environments
---

### Post by uxohus2b on 2006-07-03
Hi,

I use Ubuntu 6.06 and installed Acrobat Reader using Synaptic. For some reason, every time I open a PDF file with forms, I get a warning message that reads: 

"You cannot save data typed into this form. Please print your completed form if you would like a copy for your records."

And, indeed, AR will not save form entries. 

Does anybody know why this is happening and/or how I can fix this? 
Also, is there a program that's comparable to Adobe Reader in filling out forms?

Also just for your information: there was some conflict between scim and AR, so I had to insert "GTK_IM_MODULE=xim" to the beginning of the acroread file. This is probably irrelevant, however. In any case, I'll be grateful for any suggestions. Thanks.

---

### Post by aysiu on 2006-07-03
The *acroread* package **is** Adobe Acrobat Reader. I can attest that nothing is wrong here, as I've used Adobe Reader in Windows and Mac, too, and this same behavior happens.

It occurs because of the way the form is designed--most forms are not designed to save data but to be read-only. You can input data, print it, but then when you close, you're not allowed to save.

---

