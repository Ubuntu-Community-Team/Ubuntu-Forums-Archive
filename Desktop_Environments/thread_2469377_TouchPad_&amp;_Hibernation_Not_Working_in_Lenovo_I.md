---
title: "TouchPad &amp; Hibernation Not Working in Lenovo Ideapad S145-15IIL"
date: 2021-11-26
forum: Desktop Environments
---

### Post by slkamath on 2021-11-26
Hi,

Hope everyone are safe & doing good.

I am having Lenovo Ideapad S145-15IIL Laptop. i5, 512GB SSD, 1TB HDD, 12GB RAM.

I tried installing Ubuntu 20.04, 20.10, 21.04, 21.10. In any of these my touchpad & hibernation is not working. Checking purpose I have installed Windows 10, in this it is working fine.

I tried all the ways many people mentioned in different forum to activate Touchpad & Hibernation, but no luck. 

So can someone guide me how to solve this issue?

Thanks in advance.

Lokesh Kamath

---

### Post by ActionParsnip on 2021-11-27
Try the boot option
```

i8024.irqpoll
i8024.reset
i8024.nomux
i8024.noloop

```
Try them one at a time. I've seen these help with touch pads on Lenovo laptops

---

### Post by GhX6GZMB on 2021-11-27
Hibernate is per default disabled in (x)Ubuntu. It needs a bit of effort to get it to work. Have you defined a _swap partition_? If not, it's very difficult.

---

### Post by slkamath on 2021-12-03
> **ActionParsnip said:**
> Try the boot option
```

i8024.irqpoll
i8024.reset
i8024.nomux
i8024.noloop

```
Try them one at a time. I've seen these help with touch pads on Lenovo laptops

Thanks for your response. 
Sorry, I didnt get it. Can you please tell me where I have to type?

Lokesh Kamath

---

### Post by slkamath on 2021-12-03
> **ml9104 said:**
> Hibernate is per default disabled in (x)Ubuntu. It needs a bit of effort to get it to work. Have you defined a _swap partition_? If not, it's very difficult.


Thanks for your response.

While installing it will not ask SWAP Partition. I have created the SWAP Partition after seeing in many forums. You are right, it is too difficult.

Any other way we can do this? coz I am finding this issue only with Lenovo. In Dell & other brand's no issues. While istalling it'sself it give option of Swap for Hibernate (ubuntu21.10). So if we choose that it will directly give option of hibernation.

Lokesh Kamath

---

### Post by ActionParsnip on 2021-12-03
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

