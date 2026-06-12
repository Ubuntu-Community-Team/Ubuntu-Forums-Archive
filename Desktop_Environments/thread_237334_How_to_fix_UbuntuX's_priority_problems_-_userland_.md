---
title: "How to fix Ubuntu/X's priority problems - userland freezes lock system?"
date: 2006-08-16
forum: Desktop Environments
---

### Post by Ninjagecko on 2006-08-16
Hello.

Any help would be greatly appreciated.

Problem:
How does one make it so that all user processes ever run on the machine do not have higher priority than the GUI? Why is this not already the default?

Explanation:
Unlike Mac OS X, Kubuntu does not behave nicely when an application freezes. Sometimes when applications freeze, they freeze the entire system, and it's impossible to ctrl-alt-esc-click to force-quit a window, or to alt-tab to another program like a terminal to kill the offending process (this always happens with Wine, and sometimes AmaroK).

On Mac, this never happens. If an application is frozen, you can do three things:
1) Hitting cmd-opt-esc will always bring up a list of running processes you can force-quit.
2) On Mac the GUI never stops responding, unlike Kubuntu where the mouse may freeze and you can't access popup menus. On the Mac, you can simply move your mouse over to the dock, right-click, and select "Force-Quit", and the app will be kill -9'ed. You can even alt-tab to another process, ignoring the offending app or getting yourself a terminal to play around with. Both these things are (not always, but usually) impossible in Kubuntu.

Also, opening a ctrl-alt-f* terminal is not an option. Not only is it disruptive, but they also do not work when nVidia is enabled, and hence I never have access to them. =(

Misc.:
Would the 'nice' command help in this case?

Thank you.

---

