---
title: "How to uninstall Matlab?"
date: 2008-04-20
forum: Desktop Environments
---

### Post by ak87 on 2008-04-20
Hey!

I just tried to install MatLab on Ubuntu 8.04, but I configured it wrong a couple of times...
Now I want to uninstall it, how do I do that?

I need to remove the program, and all the contents it installed (like symlinks, license manager)

Please help

//Alex

---

### Post by phoeluns on 2008-05-20
Here's what you should do to completely uninstall MATLAB on a UNIX or Linux machine:

1. Shut down the license manager using the 'lmdown' command.

2. Remove the entire root MATLAB directory tree using the 'rm -r' command.

3. Remove the license manager files in the /var/tmp directory. These files should begin with 'lm'.

This should remove MATLAB and the License Manager completely from your UNIX or Linux machine.

If you want to remove the FLEXnet license manager, you can remove all files that begin with the letters 'lm' within the $matlab/etc and the /var/tmp directories. You can also remove any subdirectories in the $matlab/etc directory. Once this is done, the FLEXnet license manager has been removed from your MATLAB installation.

And you can get more information from:
[http://www.mathworks.com/support/solutions/data/1-17VR3.html?solution=1-17VR3](http://www.mathworks.com/support/solutions/data/1-17VR3.html?solution=1-17VR3)

---

