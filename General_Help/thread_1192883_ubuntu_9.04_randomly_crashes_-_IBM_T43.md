---
title: "ubuntu 9.04 randomly crashes - IBM T43"
date: 2009-06-20
forum: General Help
---

### Post by ntenzpunishment on 2009-06-20
Hi all,

I recently installed ubuntu 9.04 on my IBM T43 but it crashes randomly and I cant see anything in the logs. The screen freezes and I cant restart X (ctrl, alt, backspace) furthermore I cant switch to console and see output there. Only thing I can do is to hold down the power and boot.

I tried to install xorg-driver-fglrx but when I boot grub seems to crash/cant render the output (perhaps resolution or?)

I think it is a graphics problem but im not sure. I havent enabled compiz or similar.
  
Gfx:

01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]

You can see my Xorg.failsafe.log here [http://pastebin.com/m17d26464]("http://pastebin.com/m17d26464")

Any advise would be appreciated

---

### Post by pekka.lehtikoski on 2009-06-21
Hi,
Briefly: 9.04 will not work properly on Thinkpad T43, but 8.04 LTS will. 

Same story: I had same problem yesterday, trying to install 9.04 on T43. It locks up at some point when using graphic applications. I read what I could from net and ended up installing 8.04. It picked up ATI proprietary drivers automatically and all seems to be working nicely.

Reason: Difference between 8.04 and 9.04 is that these use different Xorg version. ATI proprietary driver for Mobile Raedon X300 works only with older one, and ATI has no plans to support X300 with newer Xorg. So 9.04 uses open source driver, which is not ready enough to use. 

Only hope for us to have 9.04 working on T43 in future is that someone improves the open source driver to useful level. ATI is unlikely to work on this.

Best regards,
Pekka Lehtikoski

---

### Post by ntenzpunishment on 2009-06-21
Hi pekka.lehtikoski,

Thank you so much for the answer. You just saved me a lot of time trying to fix it. I guess I have to install 8.04. Greatly appreciated.

Kind regards,

Daniel

---

