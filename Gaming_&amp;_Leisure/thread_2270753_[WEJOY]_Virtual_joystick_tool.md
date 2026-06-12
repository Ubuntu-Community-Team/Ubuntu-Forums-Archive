---
title: "[WEJOY] Virtual joystick tool"
date: 2015-03-25
forum: Gaming &amp; Leisure
---

### Post by Vantskruv on 2015-03-25
I've made a tool to read physical joystick devices, create virtual joystick devices and output keyboard presses.

I've recently uploaded this to github for those who are capable to compile it:
[https://github.com/Vantskruv/wejoy](https://github.com/Vantskruv/wejoy)

---

### Post by gionata on 2015-06-07
> **Vantskruv said:**
> I've made a tool to read physical joystick devices, create virtual joystick devices and output keyboard presses.

I've recently uploaded this to github for those who are capable to compile it:
[https://github.com/Vantskruv/wejoy](https://github.com/Vantskruv/wejoy)

Dear Vantskruv,
Your project was exactly what I was looking for (I want to use some RC simulators under Linux).
There are some problems compiling it. I solved them changing the make.sh:

linked libraries must go at the end:

g++ -std=c++11 -Wall suinput.c joystick.cc LuaScript.cc CVirtualJoy.cc CVirtualKeyboard.cc -o wejoy main.cc -ludev  -lpthread -lX11 -llua5.2

thanks a lot

---

