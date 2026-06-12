---
title: "How do I get GKrellM to show cpu temp and fan speed?"
date: 2009-04-18
forum: General Help
---

### Post by Necis on 2009-04-18
I am currently running Ubuntu 9.04 RC on a Macbook pro. I looked around and I saw some people mention Gkrellm to view cpu temp and fan speed. I am kind of new to linux and I cant figure out how to get the program to show cpu temp and fan speed. Any help would be greatly appreciated.

*edit* I use the Macbook pro 4.1 model.

---

### Post by dcstar on 2009-04-18
> **Necis said:**
> I am currently running Ubuntu 9.04 RC on a Macbook pro. I looked around and I saw some people mention Gkrellm to view cpu temp and fan speed. I am kind of new to linux and I cant figure out how to get the program to show cpu temp and fan speed. Any help would be greatly appreciated.

*edit* I use the Macbook pro 4.1 model.

Firstly, you need to install the **lm-sensors** package and then run this to set it up:

```
sudo sensors-detect
```

Then you should have sensor data to display. You can also install the **sensors-applet** package and all of this data can be displayed in a panel.

---

### Post by Necis on 2009-04-18
I tried that and it still does not show anything. Do I have to restart my computer for it to take effect?

*edit* restarted my computer. that didnt help either

---

