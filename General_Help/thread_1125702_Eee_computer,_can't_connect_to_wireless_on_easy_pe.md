---
title: "Eee computer, can't connect to wireless on easy peasy."
date: 2009-04-14
forum: General Help
---

### Post by dragos240 on 2009-04-14
Hello, I installed easy peasy on my netbook here, and it doesn't recognise wireless connections. I need to connect to wireless networks, I am connected now via ethernet connection to my router, so i'm sitting on the floor typing it. Could anyone help me? I figured out the model, it's 900HD Asus eee-pc. If someone could help me, I would be very greatful.

---

### Post by dragos240 on 2009-04-15
bump!

---

### Post by Bearded-flower on 2009-04-17
Umm i also use easy peasy umm i was talking to my freind myles and he told me that there was alot of issues with it in america.
Im not shure why and im sorry i can help

---

### Post by Bearded-flower on 2009-04-17
Bump

---

### Post by Fenris_rising on 2009-04-17
Not sure if I can help. I have a 904HD with easy peasy on it and it's never been a problem connecting to my wireless.

What encryption are you using.

Does your router show up on the wireless list.

Does your router have an option for more than 1 key usually 1-4

If so have you told the wireless control the correct key. (1-4)

Be aware of case sensitivity when entering your code

regards

Fenris

---

### Post by jtniehof on 2009-04-17
Haven't used easy peasy, but I'm assuming (based on the January release date) that it's based on Intrepid. I was unable to get wireless working on my 900HD with eeebuntu 2.0, also based on Intrepid. It works flawlessly with the Jaunty RC, though.

---

### Post by Daisuke_Aramaki on 2009-04-17
> **dragos240 said:**
> Hello, I installed easy peasy on my netbook here, and it doesn't recognise wireless connections. I need to connect to wireless networks, I am connected now via ethernet connection to my router, so i'm sitting on the floor typing it. Could anyone help me? I figured out the model, it's 900HD Asus eee-pc. If someone could help me, I would be very greatful.

Are you able to see your wireless access points? do you use a gui frontend to access your wireless, like wicd, network manager etc., or just wpa_supplicant.conf? what do you get when you issue this command on a terminal?

```
iwconfig
```

Does your wireless device node status show up?

---

### Post by dragos240 on 2009-04-18
Oh hey everyone! I have a solution! I found an eee specfic linux kernel! It fixed my problem! I hope[ this]("http://www.array.org/ubuntu/index.html") fixes everyone elses!

---

### Post by juancarlospaco on 2009-04-18
Hi, im on a eee all working* "out-of-the-box"* with Ubuntu Jaunty.

---

