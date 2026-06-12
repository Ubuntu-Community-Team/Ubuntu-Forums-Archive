---
title: "Dell Optiplex on Dapper Intel 965Q graphics mess"
date: 2007-06-16
forum: Dell  Ubuntu Support
---

### Post by whizbaby on 2007-06-16
We have about 100 dell optiplex (i think 745) with an Intel 965Q graphics chip onboard. They are running on Ubuntu 6.04 Dapper. My problem is:

- with the vesa driver I get nice disco effects when I log out or ctrl-alt-bckspc, the screen flickers pink-whitish.
- with the i810 driver the 1600x1200 resolution of the monitor is not working (all simply black). The fixing package, 915resolution namely, especially designed to cure this, doesnt know the 965Q chipset yet in the Dapper version (only from feisty on).
- the driver you can download from Intel needs a newer xorg version than Dapper has (->feisty).

any idea or a solution I dont know about? 
(apart upgrading all clients to feisty)

---

### Post by whizbaby on 2007-06-16
):P @bdaman

---

### Post by whizbaby on 2007-06-18
thesis:
its impossible to make dapper run smoothly on optiplex with 965 intel graphics chip.

---

