---
title: "Minecraft bedrock server issue"
date: 2023-12-27
forum: Gaming &amp; Leisure
---

### Post by zx10rsilver on 2023-12-27
I've setup Minecraft bedrock on Ubuntu before but this is my first attempt on a raspberry pi 4 model b

I'm a bit of a noob but the issue looks to be with qemu?

When I try to run ./bedrock_server I get error
/lib64/ld-linux-x86-64.so.2: No such file or directory

What do I need to do and again apologies I'm trying to help my son build this

---

### Post by MAFoElffen on 2023-12-27
> **zx10rsilver said:**
> I've setup Minecraft bedrock on Ubuntu before but this is my first attempt on a raspberry pi 4 model b

I'm a bit of a noob but the issue looks to be with qemu?

When I try to run ./bedrock_server I get error
/lib64/ld-linux-**[COLOR=#ff0000]x86-64[/COLOR]**.so.2: No such file or directory

What do I need to do and again apologies I'm trying to help my son build this

I would say you have the wrong package for the architecture. That error is looking for something on arch x86_amd64, and Raspberry Pi is arch arm64.

---

### Post by deadflowr on 2023-12-27
*moved to the gaming and leisure sub-forum*

---

### Post by zx10rsilver on 2023-12-28
Isn't that the point of qemu?

---

### Post by maximge on 2024-05-21
Just Download the Correct Server Version. Ensure you have the ARM-compatible version of the Minecraft Bedrock server. The x86-64 version won't run on the ARM architecture of the Raspberry Pi.

---

