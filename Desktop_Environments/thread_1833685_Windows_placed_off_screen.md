---
title: "Windows placed off screen"
date: 2011-08-26
forum: Desktop Environments
---

### Post by stallinux on 2011-08-26
Symptoms: New windows are placed slightly off screen.

Let me post this thread since I did not find it posted and I found the solution. hopefully the search engines will find it from now on (I have seen other people complain about it):

Observation: For instance when opening a pdf document it is shown in the bottom-right corner, with only one quarter visible. The other three quarters are on other desktops (the top right part on desktop 2, bottom left on desktop 3 and bottom right on desktop 4). Very annoying.

Diagnostic: This is a 'problem' ("no it is not a bug, it is a system feature") with Compiz. There must be some reasoning behind it, but it escapes me. Compiz places a new window in the center of the combined 4 desktops.

Solution: Uncheck option 'Window Management: Place Windows' in Compiz (Preferences: CompizConfig Settings Manager)

System: Ubuntu 11.04, classic desktop, Compiz

---

### Post by Enigmapond on 2011-08-26
Try playing with the Window Management area of the Compiz Manager. Scale and Re-Size may fix this issue.

---

