---
title: "Suspend in MATE Works Manually FAILS when run by PwrMGR"
date: 2018-04-18
forum: Desktop Environments
---

### Post by ubix on 2018-04-18
I'm running** Ubuntu 16.04** with multiple desktops, on three different architectures, first is an Intel Desktop, the other is an AMD Desktop and the third on Intel MacMini multi-boot system. I mostly use **GNOME Clasic Flashback**, and **Ubuntu MATE Desktop** environments, beside **Unity**, as well as, the **Xfce**. 

Recently I discovered that both, **Ubuntu-MATE** and **Xfce**, fail to suspend either of above mentioned computers when they stay idle over the limit set in their respective **Power Management windows**. However, manually suspending them either from **Power Down Window**, by pressing the **Suspend** button, or by running either **[FONT=Courier New]systemctl suspend[/FONT]** or **[FONT=Courier New]systemctl hibernate[/FONT]** from a terminal works as expected.  All the computers go to sleep or they turn off in case I run **[FONT=Courier New]systemctl hibernate[/FONT]**, and they all promptly return back to their last running state **Ubuntu MATE**, as well as **Xfce**, were in before it got suspended or put into hibernate state.

This inconsistent behaviour is only occurring in **Ubuntu MATE Desktop** GUI and in **Xfce**. Neither **GNOME Clasic Flashback**, nor **Unity** experience the same inconsistencies. They all go to sleep when they are idle for the specified permitted Idle time, and have no trouble resuming to their last running state upon waking up.  

The fact, that suspend works from the command line regardless which display manager I use, and that *automatic suspension* fails only in **Ubuntu MATE** and **Xfce**, points out that there is something very simple misconfigured in those two (MATE's, and Xfce's) *Power Management GUIs*.

Can anybody, please, give me some pointers where to turn to find a solution to this problem.
Thank you, in advance:p

---

