---
title: "Slow Redraw in 9.10"
date: 2009-12-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sevenfactorial on 2009-12-07
Hello,

I recently upgraded to 9.10 from 8.10.

Since then my computer has been performing screen redraws at an agonizingly slow rate.

When I scroll in a browser, the cpu maxes out and I still get a lot of choppy movement.

If I rapidly manipulate a window, the animation of the movement is very rough.

Does anyone have any idea what my problem might be?  My machine is an Optiplex 760 and was quite fast before the upgrade.

Thank you very much,

H.

---

### Post by mikewhatever on 2009-12-07
What graphics card do you have? have you checked System->Admin->Hardware Drivers after the upgrade? Do you have visual effects on? Try turning them of if you do.

---

### Post by sevenfactorial on 2009-12-09
I have managed to solve this problem.  The issue was that I had updated to 9.10 and was using the "fglrx" driver, which is evidently inconsistent with something.

The fix was to change to the "ati" driver.  

I found instructions here:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

