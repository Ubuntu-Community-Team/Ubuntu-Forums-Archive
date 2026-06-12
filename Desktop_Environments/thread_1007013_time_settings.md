---
title: "time settings"
date: 2008-12-10
forum: Desktop Environments
---

### Post by vasluianuliviu on 2008-12-10
i have a dual boot meaning linux instaled inside windows. with this ocasion my clock time in both sistems goes crazy. in this moment it is shows 00.18 and time is 07.18 i have instaled ntp but same story. any ideea? i can find that settings to change time to romania/bucharest like in ubuntu 8.04. i use ibex. after 10h still same situations

---

### Post by vasluianuliviu on 2008-12-12
> **vasluianuliviu said:**
> i have a dual boot meaning linux instaled inside windows. with this ocasion my clock time in both sistems goes crazy. in this moment it is shows 00.18 and time is 07.18 i have instaled ntp but same story. any ideea? i can find that settings to change time to romania/bucharest like in ubuntu 8.04. i use ibex. after 10h still same situations


no one can have an solutions for me?

---

### Post by mister_p_1998 on 2008-12-12
> **vasluianuliviu said:**
> no one can have an solutions for me?

I had this problem about a year ago on Dapper, you have to tell it to use the BIOS clock as a base time (GMT) then adjust the system time (Ubuntu time) according the the time of year (BST or GMT in UK) I think theres an option to change in the date/time settings. If you tell it to go by the bios clock only, it will keep altering the BIOS clock.

Steve

---

