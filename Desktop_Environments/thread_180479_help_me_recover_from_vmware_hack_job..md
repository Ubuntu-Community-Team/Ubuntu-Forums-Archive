---
title: "help me recover from vmware hack job."
date: 2006-05-22
forum: Desktop Environments
---

### Post by dmizer on 2006-05-22
i installed vmware and it was the biggest mistake i've ever made since installing ubuntu.  kqemu/qemu was a little laggy, and took about 5 minutes to boot win2k, but it was still usable.

in an effort to resolve a problem i've been having with trying to create a network bridge so i can get a local ip from my network in my vm, i installed vmware.  but it took literally OVERNIGHT to install windows, and it took over 20 minutes just to boot.

it hyjacked my network settings, waxed my sound conf, and forces my samba to start during the boot.  now, i uninstalled vmware to the best of my ability by running the utility found in /etc/vmware-uninstall, but i still have most of my previous issues.

since vmware seems to have chosen alternative methods for setting configurations (ex. ifconfig shows a bridge in place, but /etc/network/interfaces does not have one listed) ...

1) how do i track down the vmware config files that have hyjacked my entire system?
or
2) how do i insure that my system is using my previously (and painstakingly) configured envirnoment?

---

### Post by dmizer on 2006-05-23
okay ... let's start with just one of my problems?

networking.
on restart, my network card often does not detect dhcp.
i had to turn off ipv6 again.
even though ipv6 is turned off, once i do get a dhcp lease ... if i open anything internet related, my connection drops.
sometimes ifdown/up will fix the problem.
sometimes reloading the nic module will fix the problem.

but it's a real headache to have to mess with this nearly every time i boot.

here's my interfaces
```
# /etc/network/interface
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The bridge network interface(s)
#auto br0
#iface br0 inet dhcp
#bridge_ports eth0
#bridge_fd 1
#bridge_hello 1
#bridge_stp off


iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid ******

auto eth1

#auto eth0

auto eth0


```
it appears that there are two confiturations for my eth0.  where does that auto eth0 come from?  when it appears is when i have problems.  as you can see, i've commented it out before.

---

### Post by dmizer on 2006-05-24
this is still a big problem.  here's networking:
```
#!/bin/sh
#
# manage network interfaces and configure some networking options

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

if ! [ -x /sbin/ifup ]; then
    exit 0
fi

[ -f /etc/default/rcS ] && . /etc/default/rcS
. /lib/lsb/init-functions

spoofprotect_rp_filter () {
    # This is the best method: turn on Source Address Verification and get
    # spoof protection on all current and future interfaces.
    
    if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]; then
        for f in /proc/sys/net/ipv4/conf/*/rp_filter; do
            echo 1 > $f
        done
        return 0
    else
        return 1
    fi
}


spoofprotect () {
    if [ "$VERBOSE" != no ]; then
        log_begin_msg "Setting up IP spoofing protection..."
        spoofprotect_rp_filter
        log_end_msg $?
    else
        if ! spoofprotect_rp_filter; then
	    log_failure_msg "Failed to setup IP spoofing protection"
	fi
    fi
}

ip_forward () {
    if [ -e /proc/sys/net/ipv4/ip_forward ]; then
        if [ "$VERBOSE" != no ]; then
            log_begin_msg "Enabling packet forwarding..."
            echo 1 > /proc/sys/net/ipv4/ip_forward
            log_end_msg $?
        else
            echo 1 > /proc/sys/net/ipv4/ip_forward
        fi
    fi
}

syncookies () {
    if [ -e /proc/sys/net/ipv4/tcp_syncookies ]; then
        if [ "$VERBOSE" != no ]; then
            log_begin_msg "Enabling TCP/IP SYN cookies..."
            echo 1 > /proc/sys/net/ipv4/tcp_syncookies
            log_end_msg $?
        else
            echo 1 > /proc/sys/net/ipv4/tcp_syncookies
        fi
    fi
}

doopt () {
    optname=$1
    default=$2
    opt=`grep "^$optname=" /etc/network/options`
    if [ -z "$opt" ]; then
        opt="$optname=$default"
    fi
    optval=${opt#$optname=}
    if [ "$optval" = "yes" ]; then
        eval $optname
    fi
}

case "$1" in
    start)
	doopt spoofprotect yes
        doopt syncookies no
        doopt ip_forward no

        log_begin_msg "Configuring network interfaces..."
        type usplash_write >/dev/null 2>/dev/null && usplash_write "TIMEOUT 120" || true
        if [ "$VERBOSE" != no ]; then
            ifup -a
        else
            ifup -a >/dev/null 2>&1
        fi
        type usplash_write >/dev/null 2>/dev/null && usplash_write "TIMEOUT 15" || true
	log_end_msg $?
	;;
    stop)
        if sed -n 's/^[^ ]* \([^ ]*\) \([^ ]*\) .*$/\1 \2/p' /proc/mounts | 
          grep -q "^/ nfs$"; then
            log_failure_msg "NOT deconfiguring network interfaces: / is an NFS mount"
        elif sed -n 's/^[^ ]* \([^ ]*\) \([^ ]*\) .*$/\1 \2/p' /proc/mounts |  
          grep -q "^/ smbfs$"; then
            log_failure_msg "NOT deconfiguring network interfaces: / is an SMB mount"
	elif sed -n 's/^[^ ]* \([^ ]*\) \([^ ]*\) .*$/\2/p' /proc/mounts | 
          grep -qE '^(nfs[1234]?|smbfs|ncp|ncpfs|coda|cifs)$'; then
            log_failure_msg "NOT deconfiguring network interfaces: network shares still mounted."
        else
            log_begin_msg "Deconfiguring network interfaces..."
            if [ "$VERBOSE" != no ]; then
                ifdown -a --exclude=lo
            else
                ifdown -a --exclude=lo >/dev/null 2>&1
            fi
	    log_end_msg $?
        fi
	;;
    force-reload|restart)
	doopt spoofprotect yes
        doopt syncookies no
        doopt ip_forward no
        log_begin_msg "Reconfiguring network interfaces..."
        if [ "$VERBOSE" != no ]; then
            ifdown -a --exclude=lo
            ifup -a
        else
            ifdown -a --exclude=lo >/dev/null 2>&1
            ifup -a > /dev/null 2>&1
        fi
	log_end_msg $?
	;;
    *)
	log_success_msg "Usage: /etc/init.d/networking {start|stop|restart|force-reload}"
	exit 1
	;;
esac

exit 0

```
i have no idea what i'm looking at here.

---

### Post by dmizer on 2006-05-25
i found four networking related files left behind by vmware in /usr/bin as follows:
```
vmnet-bridge
vmnet-dhcpd
vmnet-netifup
vmnet-sniffer
```
these are apparently suppose to be called to by a file called vmware-config.pl, but that file no longer exists.

i also discovered that vmware made changes to my ip tables as follows:
```
iptables --table nat --append POSTROUTING --out-interface vmnet0 -j MASQUERADE
iptables --append FORWARD --in-interface vmnet1 -j ACCEPT
iptables -A INPUT -i vmnet1 -s 192.168.2.0/24 -d 192.168.1.1 -j ACCEPT
```
i am not sure if the iptables remain altered by vmware or not, but that's where i'm looking next.

---

### Post by dmizer on 2006-05-25
vmware wants iptables to be in /usr/bin.  i didn't find anything in /usr/bin ... but i found two references to iptables on my machine, one in sbin/, and a library containing a bunch of modules (lib/iptables).  i don't see anything marked as vmware, but i'm sure it's quite possible that vmware could have dropped a proprietary module in the directory.

am i barking up the wrong tree here?  anyone have a list of what's suppose to be in here by default, and is there a way to checksum it to see if the modules are ubuntu original?

---

### Post by dmizer on 2006-05-25
okay ... how about this?

my machine won't shut down anymore without holding the power button.  the shutdown sequence hangs on stopping dhcp server.

i am removing dhcp3-client and dhcp3-common from my packages list.

---

### Post by dmizer on 2006-05-25
okay ... that fixed most of my problems.  my computer does't automatically turn on samba anymore, and i can shutdown no problem.

but now i can't catch a dhcp lease at all.  only way i can connect is via static.  i assume that's because i removed dhcp3 client and common.

do i need both of these in order to get a dhcp lease?

---

### Post by dmizer on 2006-05-25
upon removing dhcp client and manager, synaptic also indicated that it would need to remove "network-manager" ... i installed this a while back in an effort to create a network bridge myself.  i believe network-manager and ubuntu's default network service were fighting eachother.

note however, that network-manager was installed on this machine prior to vmware and never caused a problem until after installing vmware.  i am not sure if i ever configured network-manager to manage my internet, could it be that vmware used network manager to configure it's network settings?

i have reinstalled dhcp3-client and common and i can now get a dhcp lease on reboot.  at least for now, that problem is solved.

but now that i have added my dhcp3-client back in, samba wants to restart.  how can i turn that off?

---

### Post by simonn on 2006-05-25
No help to you now, but this is what /usr/local is for i.e. installing anything that is not required for the system to boot and/or is not part of the distribution.

List of files installed by vmware player on my machine attached - I hope.

EDIT: Cannot find any evidence of vmware player install modifying any config files.

The modifcations to iptables are made via /usr/local/lib/vmware/net-services.sh so should not effect iptables on a reboot - unless there is an install option I did not use?

Blameth vmware player not for your woes, methinks.

---

### Post by dmizer on 2006-05-25
my computer worked fine before installing vmware, and no updates after vmware because it's been a bear to manage ever since.

i am definitely not saying that vmware is to blame ... in fact, i may have been the one to botch the whole thing.  but whatever happened during it's install played havoc on my system.  it may also have been that i waxed the install of vmware myself.  i really have no idea.  i'm just trying to recover from it.

now i've already discovered that part of that problem is because my system was misconfigured to begin with: ie, i installed network-manager and never configured it correctly.

but at the very least, i know ipv6 was turned back on after i installed vmware.  and i most definitely had it turned off before.

i'm no expert here, and i never claimed to be.  i'm just plodding through this trying to find my answer because i'm not getting anything from anyone else.  most likely because no one else knows the answer.  which simply means i'm on my own.  and, if nothing else, maybe someone else might be able to glean something from this thread.

if not, well ... at least i have something i can refer back to in a pinch.

thanks for the attachment ... i'll have a closer look at it and see if i can find something.

---

### Post by dmizer on 2006-05-26
okay ... fixed my last two problems.

i couldn't figure out how to disable samba from auto starting on boot, so i "fixed" it by removing it.  typical windows fix, but at least i get decent boot times now.

also to fix the sound i had to go into /etc/libao.conf and change the driver back to alsa from esd.

---

### Post by pepolez on 2006-05-30
[QUOTE=dmizer]....
it appears that there are two confiturations for my eth0.  where does that auto eth0 come from?  when it appears is when i have problems.  as you can see, i've commented it out before.[/QUOTE]

the auto eth# lines refer to interfaces included in ifdown/ifup with the -a (all) switch. for example, here is my config:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.2.3
        netmask 255.255.255.248
        broadcast 192.168.2.7

auto eth1
iface eth1 inet dhcp
```

lo of course, is the loopback interface, and is included in the -a switch

eth1 (onboard NIC) is my primary interface to get to the internet, is included in interface start/stops with the -a switch and gets it's IP via DHCP.

eth0 (PCI NIC) is my secondary interface (it's only eth0 because the PCI card is listed before the onboard in lspci), but is not connected to the internet and is instead connected to another small network with 6 IPs avaliable in the subnet. this interface is also covered by the -a switch.

---

