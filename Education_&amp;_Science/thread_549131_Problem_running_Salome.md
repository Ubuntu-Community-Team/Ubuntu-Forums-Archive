---
title: "Problem running Salome"
date: 2007-09-12
forum: Education &amp; Science
---

### Post by Hayesio on 2007-09-12
Hi everyone,

I installed Salome from the Dedian-Starge binary through the installwizard and it seems to have installled ok but i cant run it.  Whe the installwizard finished i clicked the button "Run Salome now" (or words to that effect) and it ran fine! Then i closed it.

running it again returns this:

```
jack@Star-Ship-Omega:~/salome_3.2.6/KERNEL_3.2.6/bin/salome$ runSalome
Configure parser: Warning : could not find user configuration file
Searching for a free port for naming service: 2810 - OK
Traceback (most recent call last):
  File "/home/jack/salome_3.2.6/KERNEL_3.2.6/bin/salome/runSalome.py", line 984, in ?
    clt,args = main()
  File "/home/jack/salome_3.2.6/KERNEL_3.2.6/bin/salome/runSalome.py", line 975, in main
    searchFreePort(args, save_config)
  File "/home/jack/salome_3.2.6/KERNEL_3.2.6/bin/salome/runSalome.py", line 926, in searchFreePort
    f = open(os.environ['OMNIORB_CONFIG'], "w")
IOError: [Errno 13] Permission denied: '/home/jack/.omniORB_Star-Ship-Omega_2810.cfg'

```

Any assistance would be greatly appreciated.

---

### Post by in_flu_ence on 2007-09-13
Is there any error during the installation process?

Seems a bad install to me.

also it might be omniORB error which I think there is a thread that had discussed on the solution.

That's all i get from your info.

Hope this lead you to a way.

---

