---
title: "graphic card"
date: 2009-12-18
forum: Desktop Environments
---

### Post by jhunt557 on 2009-12-18
can any one tell me how do you get ubuntu 9.10 your reconize your graphic card?

---

### Post by 3Miro on 2009-12-18
> **jhunt557 said:**
> can any one tell me how do you get ubuntu 9.10 your reconize your graphic card?

On my 2 laptops and one desktop I had to ... boot Karmic. It all is supposed to be automatic.

Have you checked System -> Settings -> Hardware Drivers?

When you say "doesn't recognize" do you mean "no video card found (i.e. no picture)" or "card runs with crappy resolution and no the way it is supposed to".

Also, what exactly is your card? Nvidia something, or ATI something or Integrated Intel something (I am asking for the model).

---

### Post by coffeecat on 2009-12-19
> **jhunt557 said:**
> can any one tell me how do you get ubuntu 9.10 your reconize your graphic card?

It would help if you explained what your problem is. Do you boot into a console with no GUI? Can you not get the correct resolution? Something else?

Also, as the previous poster points out, we need to know what your graphics card is. Post the terminal output of:

```
lspci | grep "VGA"
```

---

