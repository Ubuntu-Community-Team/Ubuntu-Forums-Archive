---
title: "ubuntu software center"
date: 2012-01-01
forum: Desktop Environments
---

### Post by shreyas_patel21 on 2012-01-01
Hi all,

I have installed ubuntu11.10 and I am new to ubuntu.

when I try to install any software using ubuntu software center,
the install button is not available to press, its not highlighted.
I have attached the screenshot of software center

I am using tatadocomo3g to connect to the internet.

why the button is not highlighted?
is it because of permissions or because of net connection?

Thank you.

---

### Post by Frogs Hair on 2012-01-01
Do you have permission to install software with that account ?  Try the following in the terminal . ```
sudo apt-get install eclipse
```

---

### Post by shreyas_patel21 on 2012-01-02
> **Frogs Hair said:**
> Do you have permission to install software with that account ?  Try the following in the terminal . ```
sudo apt-get install eclipse
```

I am able to install it through that command but I don't want to.

My problem is why the button of install is not available to press?

How to get permission to install any software through software center.

I am using administrator account.

---

### Post by cortman on 2012-01-02
> **shreyas_patel21 said:**
> I am able to install it through that command but I don't want to.

My problem is why the button of install is not available to press?

How to get permission to install any software through software center.

I am using administrator account.

Just looking at the screenshot, it doesn't look like you were online when you tried to install from the Software Center...

---

### Post by Frogs Hair on 2012-01-02
I don't think you need to enable any special repositories for Eclipse , so the software center may have been off-line off-line as suggested above  .

---

### Post by shreyas_patel21 on 2012-01-03
> **Frogs Hair said:**
> I don't think you need to enable any special repositories for Eclipse , so the software center may have been off-line off-line as suggested above  .

Thank you for reply,

but I am unable to install any software from software center,
I have given just the example of eclipse software,.

why the software center have been off-line?
how to make it on-line?

---

### Post by topsites on 2012-01-04
I see an install button just over half up the screen on the far right, above the screenshot of the software itself, I realize it looks greyed out but that is the normal look of that button, I also understand you think it is disabled but have you tried pressing it?

> **shreyas_patel21 said:**
> why the button is not highlighted?
is it because of permissions or because of net connection?

The button is not highlighted, that is because I do not know why but it should work.
Just press it, click it.

---

### Post by TBABill on 2012-01-04
Did you have Synaptic package manager or update manager open at the same time? The system can only have one of them (Software Center, Synaptic or Update Manager) in use at a time.

---

### Post by cortman on 2012-01-04
> **TBABill said:**
> Did you have Synaptic package manager or update manager open at the same time? The system can only have one of them (Software Center, Synaptic or Update Manager) in use at a time.

+1
Or any open terminals running apt commands...

---

### Post by shreyas_patel21 on 2012-02-04
> **topsites said:**
> I see an install button just over half up the screen on the far right, above the screenshot of the software itself, I realize it looks greyed out but that is the normal look of that button, I also understand you think it is disabled but have you tried pressing it?



The button is not highlighted, that is because I do not know why but it should work.
Just press it, click it.

i tried it many times

---

### Post by shreyas_patel21 on 2012-02-04
> **cortman said:**
> +1
Or any open terminals running apt commands...


no other application running..

---

