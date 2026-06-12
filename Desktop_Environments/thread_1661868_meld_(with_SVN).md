---
title: "meld (with SVN)"
date: 2011-01-07
forum: Desktop Environments
---

### Post by nshiell on 2011-01-07
Hi running meld on a new VBox running XUbuntu
When I try and run a diff between svn working copy of a file and the SVN version

The file doesn't open and on the command shell I see: -
```
Traceback (most recent call last):
  File "/usr/lib/meld/meld/task.py", line 130, in iteration
    ret = task()
  File "/usr/lib/meld/meld/vcview.py", line 362, in run_diff_iter
    self.show_patch(prefix, patch)
  File "/usr/lib/meld/meld/vcview.py", line 499, in show_patch
    if misc.write_pipe(patchcmd, patch) == 0:
  File "/usr/lib/meld/meld/misc.py", line 242, in write_pipe
    proc = subprocess.Popen(command, stdin=subprocess.PIPE, stdout=subprocess.PIPE)
  File "/usr/lib/python2.6/subprocess.py", line 623, in __init__
    errread, errwrite)
  File "/usr/lib/python2.6/subprocess.py", line 1141, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
```

I have tried v1.3.2 (the version installed throug deb)
and v5.0.1

Same behaivour.
The only workaround at the moment is to run
```
svn diff
```
then use ```
diffuse
``` on the files

---

