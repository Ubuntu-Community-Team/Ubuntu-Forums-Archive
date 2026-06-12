---
title: "Sync palm treo 680 via bluetooth, Network error 0x030B on Treo."
date: 2006-12-31
forum: Desktop Environments
---

### Post by paultjeb on 2006-12-31
Thanks to this forum i am able now to send and receive files (photos) from amd to my Treo. 
I would also like to sync via bluetooth. To achieve this there is an excellent HOWTO at [http://www.newt.com/debian/treo650.html](http://www.newt.com/debian/treo650.html)
Setting it all up goes well untill The last item under the header 'Create a new network'.
I get ther error: 'Error:Serial:  (0x030B)'

Can someone give me a hint on how to proceed?

---

### Post by amenon on 2007-01-05
The reason for the error is that the dund daemon does not actually start when the bluetooth script is run (/etc/init.d/bluetooth) (See [bug# 75691]("https://launchpad.net/ubuntu/+source/bluez-utils/+bug/75691") ).

Edit the file /etc/init.d/bluetooth and change the line > test -f /etc/default/bluez-utils && . /etc/default/bluez-utils to > test -f /etc/default/bluetooth && . /etc/default/bluetooth will fix this. I did this with my Tungsten T5 and got it to work.

If you need to debug your connection, start dund manually. > dund --nodetach --listen --persist --msdun call <profile_name>

---

### Post by bashir783 on 2007-06-14
> **amenon said:**
> The reason for the error is that the dund daemon does not actually start when the bluetooth script is run (/etc/init.d/bluetooth) (See [bug# 75691]("https://launchpad.net/ubuntu/+source/bluez-utils/+bug/75691") ).

Edit the file /etc/init.d/bluetooth and change the line  to  will fix this. I did this with my Tungsten T5 and got it to work.


I think that problem had already been solved in the most recent version of /etc/init.d/bluetooth.

I am having the exact same problem as the original poster with my Treo 680 and Feisty.  The strange thing is that it worked at first (I was able to sync a few times) when I followed the instructions at [http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html](http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html).

But when I restarted the computer, I began receiving the 0x030B error when trying to sync.  I can still send files to my computer just fine -- it's a sync issue.

Any help would be appreciated.

---

### Post by bashir783 on 2007-06-14
Actually, I followed the instructions at [http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html](http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html) from scratch again, and now I get past the error (0x030B). 

But now the sync hangs at "Connecting with the desktop using <connection_name>."

---

### Post by amenon on 2007-06-20
I found that with Fiesty, some things have changed and my previous settings didnt work. Although, the bluetooth script starts dund with the provided options, I found that I need to manually start it for it to work.

Try
```
sudo killall dund
sudo dund --nodetach --listen --persist --msdun call <profile_name>

```
and try syncing. If that works, then all you have to do is add the following to the bottom of the */etc/init.d/bluetooth* script:

```

esac

[B]# Adding these lines because for some reason dund needs to be manually restarted
killall dund
sleep 1
/usr/bin/dund --listen --persist --msdun call palm
[/B]
exit 0

```

There is probably a better way to do this, but this works for me.

---

### Post by bashir783 on 2007-06-21
> **amenon said:**
> I found that with Fiesty, some things have changed and my previous settings didnt work. Although, the bluetooth script starts dund with the provided options, I found that I need to manually start it for it to work.

Try
```
sudo killall dund
sudo dund --nodetach --listen --persist --msdun call <profile_name>

```
and try syncing. If that works, then all you have to do is add the following to the bottom of the */etc/init.d/bluetooth* script:

```

esac

[B]# Adding these lines because for some reason dund needs to be manually restarted
killall dund
sleep 1
/usr/bin/dund --listen --persist --msdun call palm
[/B]
exit 0

```

There is probably a better way to do this, but this works for me.

Thanks.  I tried, but it didn't solve my problem.

---

### Post by greg963 on 2008-01-13
If anyone else comes across this problem see:
[https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/121915](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/121915)

I added 
sleep 1

to /etc/init.d/bluetooth in two places,

after these lines (in cases start and restart)

        start-stop-daemon --start --quiet --exec $HCID -- $HCID_OPTIONS || true
        log_progress_msg "$HCID_NAME"
        sleep 1

---

### Post by borahshadow on 2008-04-13
I too had this problem although slightly different error code on a tungsten T|3. I got it to work for a few times manually starting dund and then that quit working so I tried the sleep trick and that didn't work but then I just unplugged my bluetooth adapter and put it back in and it worked. FYI

---

### Post by Saturn Lad on 2008-04-19
Thanks greg, this fixed the problem I was having with dund not starting correctly.

---

### Post by bujutsukai on 2008-05-10
So, I'm not able to resolve with all of the great info in this post.  Maybe someone's got something left?

I did the steps mentioned above in the post (set up connection and network on my palm), but when I try to connect, my phone returns this message:

Error: GPRS connection not available...0x7143.

Of course, I set up the connection as Bluetooth and chose my trusted laptop to connect to.  I'm trying this on the Palm 685/690 Centro.  Should work the same as the 680, no?

Any advice would be appreciated.  It sinks fine with a cable, but BT would sure be nice.

---

### Post by ectospasm on 2008-07-15
> **bujutsukai said:**
> ...Error: GPRS connection not available...0x7143....


I get the same error as well.  Now, my Treo 680 works fine with my other Kubuntu system, the only difference is the Bluetooth dongles on the machines.  The one that doesn't work is a Kinamax Bluetooth 1.2 dongle (which I'm convinced isn't worth the $10 I paid for it).  The one that works is a Rocketfish Bluetooth 2.0 dongle that came with my Bluetooth keyboard and mouse combo.

---

