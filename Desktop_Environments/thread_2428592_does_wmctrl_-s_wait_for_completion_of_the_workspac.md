---
title: "does wmctrl -s wait for completion of the workspace switch?"
date: 2019-10-06
forum: Desktop Environments
---

### Post by Skaperen on 2019-10-06
i am coding a script to run programs in a particular workspace.  it first invokes [COLOR=#0000cd][FONT=courier new]**wmctrl -s ${workspace}**[/FONT][/COLOR] to switch to the desired workspace.  but it can take time to switch workspace, have the previous windows hidden, and have target workspace windows exposed.  what i am wanting to know is whether it waits for this to be complete before exiting or if the window manager could still be doing it when the script resumes.

---

