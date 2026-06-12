---
title: "Java Minecraft on Ubuntu Linux Crashes whole computer"
date: 2020-05-13
forum: Gaming &amp; Leisure
---

### Post by webmanoffesto on 2020-05-13
Java Minecraft on Ubuntu Linux laptop keeps crashing.

Can you tell me if this an Ubuntu problem or a Java problem, or a problem with the graphics processor? If it's not the GPU then please tell me what else might be causing the crashes.

After these crashes I have to restart the computer.

When the crash happens I see on the screen
"Mounted Mount unit for gnome-3-26-1604, revison 90 ..."
and
"Started Dispatcher daemon for systemd-networkd ...."

And the system is frozen on that screen

What logs should I check? Is there a Java log for me to check? What Ubuntu log might I check?

This post is the one that told me it might be the GPU.
"Why does a Java crash occur while playing Minecraft?"
[https://www.java.com/en/download/help/minecraft_error.xml](https://www.java.com/en/download/help/minecraft_error.xml)
=====.

Computer:

[LIST]
[*]Ubuntu 18.04.4 LTS
[*]Memory: 16GB RAM
[*]Processor: Intel Core i3-6100UCPU@2.30GHz x 4
[*]Graphics: Intel HD Graphics 520 SkylakeGT2
[*]OS Type: 64-bit
[*]Disk: 500GB4
[*]OpenJDK version 11.0.7 2020-04-14
[*]OpenJDK Runtime Environment build 11.0.7+10-post-Ubuntu-2ubuntu218.04
[*]OpenJDK 64-Bit Server VM (build 11.0.7+10=-post-Ubuntu-2ubunt, mixed mode, sharing)
[*]MInecraft: Java Edition 1.15.2
[/LIST]
=====.

```
$ lspci -vnn | grep VGA -A 12
00:02.0 VGA compatible controller [0300]: Intel Corporation Skylake GT2 [HD Graphics 520] [8086:1916] (rev 07) (prog-if 00 [VGA controller])
    Subsystem: CLEVO/KAPOK Computer Skylake GT2 [HD Graphics 520] [1558:2425]
    Flags: bus master, fast devsel, latency 0, IRQ 128
    Memory at de000000 (64-bit, non-prefetchable) 
    Memory at c0000000 (64-bit, prefetchable) 
    I/O ports at f000 <span style="font-size: 64px;">
    [virtual] Expansion ROM at 000c0000 [disabled] 
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:14.0 USB controller [0c03]: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller [8086:9d2f] (rev 21) (prog-if 30 [XHCI])
    Subsystem: CLEVO/KAPOK Computer Sunrise Point-LP USB 3.0 xHCI Controller [1558:2425]
```
========.

```
$ sudo lshw -numeric -C display
  *-display                 
       description: VGA compatible controller
       product: Skylake GT2 [HD Graphics 520] [8086:1916]
       vendor: Intel Corporation [8086]
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:128 memory:de000000-deffffff memory:c0000000-cfffffff ioport:f000(size=64) memory:c0000-dffff
```
=====.

```
$ sudo dmidecode -t baseboard | grep -i 'Product'
[sudo] password for tom: 
    Product Name: Lemur        
```
=====.

```
$ inxi -M
Machine:   Device: laptop System: System76 product: Lemur v: lemu6 serial: N/A
           Mobo: System76 model: Lemur v: lemu6 serial: N/A
           UEFI: American Megatrends v: 1.05.06RS76 date: 11/29/2015
```
=====.

---

### Post by mastablasta on 2020-05-14
have you tried with oracle java?

i have no issues.

---

### Post by Hwæt on 2020-05-18
IIRC Spigot and like mods still recommend JVM 8. Notch recommended the Sun VM at the time, but I never personally encountered issues with OpenJDK.

You [can download JVM 8 here]("https://www.oracle.com/java/technologies/javase-jre8-downloads.html"). You'll should uninstall your existing Java. If you don't want to do that, let me know and I can help.

---

### Post by mastablasta on 2020-05-18
actually you can have both javas installed and one is used (selected as default)

---

### Post by Hwæt on 2020-05-18
That's true, thanks! I probably should of mentioned that, I just didn't want to complicate the situation with JRE_HOME and PATH, or shell scripts, if he didn't need those things.

---

### Post by mastablasta on 2020-05-19
well if this is still an issue you need to install Oracle Java manually. the easiest way is to use a script. the procedure is:
1. you download the script and install it - or better yet add the PPA for ubuntu --> [https://launchpad.net/~linuxuprising/+archive/ubuntu/java](https://launchpad.net/~linuxuprising/+archive/ubuntu/java)
2. you then download java source package and move it to specific folder ([COLOR=#545454][FONT=Consolas]/var/cache/oracle-jdk11-installer-local/)[/FONT][/COLOR]
3. you run the update, the script will pickup the package and install it.

when it is time to update java the script will tell you to download the new source package. and then the procedure is basically repeated as you replace the old source file with the new one.

more on this here: [https://www.linuxuprising.com/2019/02/install-any-oracle-java-jdk-version-in.html](https://www.linuxuprising.com/2019/02/install-any-oracle-java-jdk-version-in.html)
another how to here (along with versions management): [https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-on-ubuntu-18-04)

and the script is here: [https://github.com/chrishantha/install-java](https://github.com/chrishantha/install-java)

the reason why it is now so complicated (before we would just add a PPA and everything would be done in software center) is because Oracle changed the policy on Java usage. now you have to register at Oracle and swear to them that this is just for personal use, just to download the java package. since you need to do this every update and since oracle hasn't provided an API this script thing was the easiest way they could automate it, i guess. and it's only a bit overwhelming the first time you do it.

---

