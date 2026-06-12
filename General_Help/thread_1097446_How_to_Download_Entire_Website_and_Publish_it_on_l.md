---
title: "How to Download Entire Website and Publish it on local network"
date: 2009-03-16
forum: General Help
---

### Post by albasheers on 2009-03-16
Do anyone know a application to download entire website and publish it on 
local network .
I tried **WebHttrack** and **Wget**, it doesn't work 
Can anyone tell me a better and easy application?

---

### Post by mb_webguy on 2009-03-16
Why exactly did WebHTTrack not work?

If you're trying to download a website that uses server-side scripting, you'd need administrative access to the webserver in order to copy the scripts themselves.  Otherwise, you're only going to be able to copy the output of those scripts which won't do you much good.

---

### Post by albasheers on 2009-03-16
when ever i download full website i am not able redirect to all the links 
 
i am getting errors like page not found

---

### Post by mb_webguy on 2009-03-16
Yeah, that's likely due to server-side scripting.  Nothing client-side is going to help you get past that.

---

### Post by albasheers on 2009-03-16
don't we have any other application  in ubuntu

---

### Post by orlox on 2009-03-16
As mentioned in the previous post, the outcome of any possible program that would do this depends on the web page itself. If it has a complex structure with many server-side actions and AJAX and all sort of stuff, youll probably get nothing good. What page are you actually trying to download???

---

