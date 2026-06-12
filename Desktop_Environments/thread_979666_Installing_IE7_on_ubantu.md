---
title: "Installing IE7 on ubantu"
date: 2008-11-12
forum: Desktop Environments
---

### Post by nitheesh86 on 2008-11-12
Hi all


I want to install ie7 for testing Purpose.I have Used IE4Linux to install ie7. i have succesfully installed ie6 and ie7.ie 6 is working fine but ie7 is not working fine. when i run ie7 i am geeting this error 

"This Operation has been cancelled due to restricions on this computer.please contact your system administrator".I am not able to Browse via ie7
 
 Any one has idea..

---

### Post by nitheesh86 on 2008-11-13
Can any one help as soon as Possible about this error

---

### Post by nitheesh86 on 2008-11-13
Can any one help as soon as Possible about this error

---

### Post by S.nazari on 2008-11-14
Give us, some more info. 
What are the instructions you are using? 
Are they here?
[http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)
That I for edgy. I'm also looking for intrepid. Are you suing edgy / feisty or intrepid? 

Thanks

---

### Post by nitheesh86 on 2008-11-14
> **S.nazari said:**
> Give us, some more info. 
What are the instructions you are using? 
Are they here?
[http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)
That I for edgy. I'm also looking for intrepid. Are you suing edgy / feisty or intrepid? 

Thanks
Yes I have Used the Same instruction link given by you.i have successfully installed  IE7 ,But i am not able browse anything. if i click on tools option i am getting this error  "This Operation has been cancelled due to restricions on this computer.please contact your system administrator"

---

### Post by mike010 on 2008-11-15
Why would you do something like this?Firefox comes with ubuntu
firefox is a lot better anyway and i don't think microsoft or anyone makes IE for linux.

---

### Post by Cammy on 2008-11-15
> **mike010 said:**
> Why would you do something like this?Firefox comes with ubuntu
firefox is a lot better anyway and i don't think microsoft or anyone makes IE for linux.

Perhaps he's a web developer and he needs to test his pages in IE to make sure they look the same across browsers.

I do web development by trade and I have this same problem.  I've sort of solved it with the very useful IE NetRenderer add-on for Firefox.

[https://addons.mozilla.org/en-US/firefox/addon/6455](https://addons.mozilla.org/en-US/firefox/addon/6455)

It allows you to render web pages in various browsers, including a few versions of IE.  Maybe this will fill the OP's need.

---

### Post by mike010 on 2008-11-16
> **Cammy said:**
> Perhaps he's a web developer and he needs to test his pages in IE to make sure they look the same across browsers.

I do web development by trade and I have this same problem.  I've sort of solved it with the very useful IE NetRenderer add-on for Firefox.

[https://addons.mozilla.org/en-US/firefox/addon/6455](https://addons.mozilla.org/en-US/firefox/addon/6455)

It allows you to render web pages in various browsers, including a few versions of IE.  Maybe this will fill the OP's need.

sounds like he needs to try that thats cool and way better then using ie7
some webpages don't display in firefox for me but no more then what it is i 
can live with it i used windows once but got fed up with all the viruses that came with running it.

---

### Post by Cammy on 2008-11-16
Well, IE Netrendered isn't perfect.  You can't test anything like Javascript because it just gives you a snapshot of the page, but since I do Gov't work, we're not allowed to use JS or anything fancy, so for checking the visual aspects, it works fine.

Also, I've run into some pages that are so poorly coded, they don't render in FF, Opera, or Konqueror, but work fine in IE, and since they aren't pages I have any control over (i.e. my old bank's online account access system) it was IE or hop in the car and drive to the bank in person.

There are all sorts of reasons why the OP may want to have access to IE.  Not everyone makes an effort to code their web pages properly.


@nitheesh86: That message sounds like IE thinks you don't have rights to use the browser.  Maybe there's some sort of permissions problem.  Have you tried running IE7 as root?

---

### Post by nitheesh86 on 2008-11-17
Thanks for the Solution .It Works fine for me

---

### Post by hartog on 2008-11-17
> **nitheesh86 said:**
> Thanks for the Solution .It Works fine for me

If you truly are a webdeveloper, you should consider using a virtual machine. IE's integration with Windows is so narrow that behaviour of the fine browser from Redmond changes along with Windows updates (which seem to have nothing @all related with IE).

Running something like VirtualBox ([http://virtualbox.org](http://virtualbox.org) || % sudo apt-get install virtualbox-ose) with windows inside gives you a much better view on your website then IErenderer.

I have seen the funkiest of differences in behavior (of both CSS and JavaScript) on different browser/os combinations all including the words "IE" and "Windows"

---

