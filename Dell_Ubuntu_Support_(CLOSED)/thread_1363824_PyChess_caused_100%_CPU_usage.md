---
title: "PyChess caused 100% CPU usage"
date: 2009-12-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cybrsaylr on 2009-12-24
Thought I'd pass this along.

Was playing PyChess earlier today. Left it running after leaving it awhile just pausing it. Came back about an hour later to resume and started another game against the PC. Noticed it running slow and not very responsive. This is very unusual for a new i7. Then I noticed a smell of electrical component 'heat' you smell when some parts get too warm! Checked System Monitor and all 8 cores showed 100% CPU usage! Checked the processes running and there were several entries for PyChess showing ~96% use! Had a bit of trouble ending the processes for that app and ended up just quiting PyChess which seemed to correct this issue. 

Is there any issues with PyChess? 
Anyone have any ideas why it caused 100% CPU use on all the i7 cores?
Ram used only went up to 1.3GB while the CPU usage was at 100%.
The PC did feel warmer than usual. This is the first time it got that warm.

---

### Post by urmomsgoat on 2010-02-15
The using 100% CPU is intentional. If you have an analyzer enabled in the PyChess preferences and you are playing a game, and the game is running (not paused via "Actions" > "Pause") and "View" > "Hint Mode" is turned on, you are telling PyChess you want your configured analyzer to do it's best to find the best move. Closing the tab for the game should kill any analyzers and stop the CPU usage. The whole system is not by any means perfect, but, it is getting better and better. See [http://code.google.com/p/pychess/issues/detail?id=526](http://code.google.com/p/pychess/issues/detail?id=526)

---

