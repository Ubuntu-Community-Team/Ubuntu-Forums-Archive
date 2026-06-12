---
title: "F5 hijacked by what? See screenshot"
date: 2012-10-25
forum: Desktop Environments
---

### Post by souptown on 2012-10-25
I can't use F5 to refresh my web browser. When I hit F5 the attached image shows up below the system area in the upper right (Unity). I have not been able to locate what F5 is been mapped to by searching through the system keyboard bindings or looking through many configs in CompizConfig.

[IMG]http://i.imgur.com/FefCW.png[/IMG]

What is that an image of, and how do I get F5 back to normal?

Thanks,
Matt

---

### Post by 2F4U on 2012-10-25
What are your hardware specs? What version of Ubuntu are you using?

---

### Post by souptown on 2012-10-25
You asked the right question! At first I thought "hardware specs? ok ...". But I went ahead and installed hwinfo and ran it. I saw:
  /dev/input/event4    Apple Keyboard

I have an Intel i3 homebrew, but I like the feel of the Apple keyboard. It had not occurred to me that this might be the issue. Google brought up [https://help.ubuntu.com/community/AppleKeyboard]("https://help.ubuntu.com/community/AppleKeyboard") which shows how to correct the function key behavior.

BTW, it's probably not relevant at this point, but I'm running Ubuntu 12.10.

Thanks so much!
Matt

---

