---
title: "Panel Application Launcher fails to Launch Application in Ubuntu 10.04"
date: 2011-04-23
forum: Desktop Environments
---

### Post by Tarion on 2011-04-23
So I put a launcher for an application (matlab) on my panel, but when I click it, it begins to launch matlab, showing a start up window, but then about when the main application would start up, the launch window disappears and nothing further happens.  

Matlab is installed and works fine, I can start it up from commandline with the command "matlab", or the full path "/usr/local/bin/matlab", but using these in the "command" portion of the launcher results in the above behavior.  

I know this isn't greatly descriptive of the overall problem, but I'm not sure what additional information would help diagnose the problem, so I'm open to suggestions.  It's not an urgent problem since I can launch it from command line. Also, other launchers seem to work.

---

### Post by physicz on 2011-05-02
Try the following command:

path/to/file/matlab -desktop

---

