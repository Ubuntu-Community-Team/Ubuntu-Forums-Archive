---
title: "Vmware Server Make Error"
date: 2006-07-10
forum: Desktop Environments
---

### Post by TriggerHappyChewie on 2006-07-10
I'm stuck on this error while making the module:

```
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config11/vmmon-only'
make -C /usr/src/linux/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-25-686'
  CC [M]  /tmp/vmware-config11/vmmon-only/linux/driver.o
In file included from include/linux/module.h:10,
                 from /tmp/vmware-config11/vmmon-only/linux/driver.c:12:
include/linux/sched.h:717: error: syntax error before ‘prio_array_t’
include/linux/sched.h:717: warning: no semicolon at end of struct or union
include/linux/sched.h:751: error: syntax error before ‘:’ token
include/linux/sched.h:792: error: syntax error before ‘:’ token
include/linux/sched.h:877: error: syntax error before ‘}’ token
include/linux/sched.h: In function ‘process_group’:
include/linux/sched.h:881: error: dereferencing pointer to incomplete type
include/linux/sched.h: In function ‘pid_alive’:
include/linux/sched.h:894: error: dereferencing pointer to incomplete type
include/linux/sched.h: In function ‘dequeue_signal_lock’:
include/linux/sched.h:1064: error: dereferencing pointer to incomplete type
include/linux/sched.h:1066: error: dereferencing pointer to incomplete type
include/linux/sched.h: In function ‘on_sig_stack’:
include/linux/sched.h:1112: error: dereferencing pointer to incomplete type
include/linux/sched.h:1112: error: dereferencing pointer to incomplete type
include/linux/sched.h: In function ‘sas_ss_flags’:
include/linux/sched.h:1117: error: dereferencing pointer to incomplete type
include/linux/sched.h: At top level:
include/linux/sched.h:1161: error: ‘exit_signal’ redeclared as different kind of symbol
include/linux/sched.h:747: error: previous declaration of ‘exit_signal’ was here
include/linux/sched.h: In function ‘thread_group_empty’:
include/linux/sched.h:1224: error: dereferencing pointer to incomplete type
include/linux/sched.h: In function ‘task_lock’:
include/linux/sched.h:1243: error: dereferencing pointer to incomplete type
include/linux/sched.h: In function ‘task_unlock’:
include/linux/sched.h:1248: error: dereferencing pointer to incomplete type
include/linux/sched.h: In function ‘setup_thread_stack’:
include/linux/sched.h:1257: error: dereferencing pointer to incomplete type
include/linux/sched.h:1257: error: dereferencing pointer to incomplete type
include/linux/sched.h:1258: error: dereferencing pointer to incomplete type
include/linux/sched.h: In function ‘end_of_stack’:
include/linux/sched.h:1263: error: dereferencing pointer to incomplete type
include/linux/sched.h: In function ‘set_tsk_thread_flag’:
include/linux/sched.h:1273: error: dereferencing pointer to incomplete type
include/linux/sched.h: In function ‘clear_tsk_thread_flag’:
include/linux/sched.h:1278: error: dereferencing pointer to incomplete type
include/linux/sched.h: In function ‘test_and_set_tsk_thread_flag’:
include/linux/sched.h:1283: error: dereferencing pointer to incomplete type
include/linux/sched.h: In function ‘test_and_clear_tsk_thread_flag’:
include/linux/sched.h:1288: error: dereferencing pointer to incomplete type
include/linux/sched.h: In function ‘test_tsk_thread_flag’:
include/linux/sched.h:1293: error: dereferencing pointer to incomplete type
include/linux/sched.h: In function ‘task_cpu’:
include/linux/sched.h:1364: error: dereferencing pointer to incomplete type
include/linux/sched.h: In function ‘set_task_cpu’:
include/linux/sched.h:1369: error: dereferencing pointer to incomplete type
include/linux/sched.h: In function ‘frozen’:
include/linux/sched.h:1411: error: dereferencing pointer to incomplete type
include/linux/sched.h: In function ‘freezing’:
include/linux/sched.h:1419: error: dereferencing pointer to incomplete type
include/linux/sched.h: In function ‘freeze’:
include/linux/sched.h:1428: error: dereferencing pointer to incomplete type
include/linux/sched.h: In function ‘thaw_process’:
include/linux/sched.h:1437: error: dereferencing pointer to incomplete type
include/linux/sched.h: In function ‘frozen_process’:
include/linux/sched.h:1449: error: dereferencing pointer to incomplete type
include/linux/sched.h:1449: error: dereferencing pointer to incomplete type
In file included from include/linux/hardirq.h:6,
                 from include/linux/interrupt.h:11,
                 from /tmp/vmware-config11/vmmon-only/linux/driver.c:20:
include/linux/smp_lock.h: In function ‘reacquire_kernel_lock’:
include/linux/smp_lock.h:36: error: dereferencing pointer to incomplete type
In file included from include/linux/mm.h:15,
                 from include/linux/poll.h:11,
                 from /tmp/vmware-config11/vmmon-only/linux/driver.c:25:
include/linux/fs.h: In function ‘get_fs_excl’:
include/linux/fs.h:876: error: dereferencing pointer to incomplete type
include/linux/fs.h: In function ‘put_fs_excl’:
include/linux/fs.h:881: error: dereferencing pointer to incomplete type
include/linux/fs.h: In function ‘has_fs_excl’:
include/linux/fs.h:886: error: dereferencing pointer to incomplete type
In file included from include/linux/poll.h:11,
                 from /tmp/vmware-config11/vmmon-only/linux/driver.c:25:
include/linux/mm.h: In function ‘can_do_mlock’:
include/linux/mm.h:649: error: dereferencing pointer to incomplete type
In file included from /tmp/vmware-config11/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config11/vmmon-only/linux/driver.c:49:
/tmp/vmware-config11/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config11/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config11/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config11/vmmon-only/linux/driver.c:49:
/tmp/vmware-config11/vmmon-only/./include/compat_wait.h: At top level:
/tmp/vmware-config11/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’include/linux/poll.h:45: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config11/vmmon-only/linux/driver.c:145: warning: initialization from incompatible pointer type
/tmp/vmware-config11/vmmon-only/linux/driver.c:149: warning: initialization from incompatible pointer type
/tmp/vmware-config11/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config11/vmmon-only/linux/driver.c:1352: error: dereferencing pointer to incomplete type
/tmp/vmware-config11/vmmon-only/linux/driver.c:1652: error: dereferencing pointer to incomplete type
/tmp/vmware-config11/vmmon-only/linux/driver.c:1652: error: dereferencing pointer to incomplete type
/tmp/vmware-config11/vmmon-only/linux/driver.c:1653: error: dereferencing pointer to incomplete type
/tmp/vmware-config11/vmmon-only/linux/driver.c:1653: error: dereferencing pointer to incomplete type
/tmp/vmware-config11/vmmon-only/linux/driver.c:1654: error: dereferencing pointer to incomplete type
/tmp/vmware-config11/vmmon-only/linux/driver.c:1654: error: dereferencing pointer to incomplete type
/tmp/vmware-config11/vmmon-only/linux/driver.c:1655: error: dereferencing pointer to incomplete type
/tmp/vmware-config11/vmmon-only/linux/driver.c:1655: error: dereferencing pointer to incomplete type
/tmp/vmware-config11/vmmon-only/linux/driver.c:1657: error: dereferencing pointer to incomplete type
/tmp/vmware-config11/vmmon-only/linux/driver.c:1970: error: dereferencing pointer to incomplete type
/tmp/vmware-config11/vmmon-only/linux/driver.c: In function ‘LinuxDriverError’:
/tmp/vmware-config11/vmmon-only/linux/driver.c:2051: error: dereferencing pointer to incomplete type
make[2]: *** [/tmp/vmware-config11/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config11/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-25-686'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config11/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

```
patrick@dvorak:~/Downloads/vmware-server-distrib$ uname -r
2.6.15-25-686

```

My linux-headers are installed also.

Any ideas?

---

### Post by Graphix on 2006-07-11
make sure you have the latest kernal then type in terminal
 ```
sudo apt-get install linux-headers-`uname -r` build-essential
```

regards
Graphix

---

### Post by TriggerHappyChewie on 2006-07-11
I already have the headers installed, as stated at the bottom of my post, and build-essential is already installed.

---

### Post by BungaMan on 2006-07-11
try to reinstall the headers, maybe first check out the file itself if you know anything about C..

---

### Post by TriggerHappyChewie on 2006-07-11
Well, there's a new kernel version + headers in the repo today, I'm going to try that.

---

### Post by TriggerHappyChewie on 2006-07-11
I think it might be a problem with gconf....

---

### Post by TriggerHappyChewie on 2006-07-11
Alright!  It works now.  I'm not sure if it was the update or me fixing gconf...

---

