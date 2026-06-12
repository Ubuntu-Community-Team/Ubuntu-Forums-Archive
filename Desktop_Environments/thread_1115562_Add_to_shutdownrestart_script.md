---
title: "Add to shutdown/restart script"
date: 2009-04-03
forum: Desktop Environments
---

### Post by bucketoftruth on 2009-04-03
Sometimes I forget that I have a VMWare guest running and I shutdown my computer.  The next time I start my vmware guest it takes as much as 30 minutes of intense CPU and disk grinding to finish booting.  To avoid making this mistake I'd like to include in the host shutdown procedure the following command:
```
vmrun -T server -h https://localhost:8333/sdk -u name -p password suspend "[standard] foldername/vmimage.vmx"
```
Where would I put this to insure that the guest image is suspended correctly before the host machine shuts down or restarts?  I use the shutdown option from the system menu.

Ubuntu 8.10, 32bit, vmrun version 2.0.0 build-122956

---

### Post by Giblet5 on 2009-04-03
First, you need to get VMware to suspend any open VMs on receipt of SIGTERM (sent to everything during shutdown, or when you log off).

We don't have the VMware code, so you know who you need to start pestering. ;)

It's a good idea, too.

---

### Post by bucketoftruth on 2009-04-12
What if I add a stop function to /etc/init.d/rc.local:

```
do_stop() {
vmrun -T server -h https://localhost:8333/sdk -u name -p password suspend "[standard] foldername/vmimage.vmx"
}

```

And modify the STOP case below as:
```

case "$1" in
    start)
        do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        [COLOR="Red"]do_stop[/COLOR]
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
```

Does the syntax look right?  Shouldn't this issue a "vmrun suspend" command to the VM guest upon shutdown of the linux host?

---

### Post by bucketoftruth on 2009-04-13
Yup, that works.

---

