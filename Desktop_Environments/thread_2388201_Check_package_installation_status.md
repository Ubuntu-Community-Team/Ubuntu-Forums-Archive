---
title: "Check package installation status"
date: 2018-03-30
forum: Desktop Environments
---

### Post by sdbhabal on 2018-03-30
Hello Experts,

I wanted to confirm 'icedtea-plugin' is installed in my Ubuntu 16.04 desktop.
Is there any way to check this?

Regards
SDB.

---

### Post by ajgreeny on 2018-03-30
The terminal command ```
dpkg -l icedtea*
``` will tell you.

For example this is what I see
```
dpkg -l icedtea*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                     Version           Architecture      Description
+++-========================-=================-=================-=====================================================
ii  icedtea-8-plugin:amd64   1.6.2-3ubuntu1    amd64             web browser plugin based on OpenJDK and IcedTea to ex
un  icedtea-gcjwebplugin     <none>            <none>            (no description available)
ii  icedtea-netx:amd64       1.6.2-3ubuntu1    amd64             NetX - implementation of the Java Network Launching P
ii  icedtea-netx-common      1.6.2-3ubuntu1    all               NetX - implementation of the Java Network Launching P
un  icedtea-plugin           <none>            <none>            (no description available)
un  icedtea6-plugin          <none>            <none>            (no description available)

```
The **un** at the start of the lines of output shows it is **uninstalled**.
If you have any icedtea package installed it will show **ii** in place of the **un** as mine does.

I can not see what this query has to do with the thread title so I have edited that accordingly.

---

### Post by oldos2er on 2018-03-30
You can also use ```
apt policy icedtea-plugin
```

---

### Post by sdbhabal on 2018-04-02
In my case below is the output.

```

**sudo dpkg -l icedtea***
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                               Version                Architecture           Description
+++-==================================-======================-======================-==========================================================================
un  icedtea-6-plugin                   <none>                 <none>                 (no description available)
un  icedtea-7-plugin                   <none>                 <none>                 (no description available)
ii  icedtea-8-plugin:amd64             1.6.2-3ubuntu1         amd64                  web browser plugin based on OpenJDK and IcedTea to execute Java applets
un  icedtea-9-plugin                   <none>                 <none>                 (no description available)
un  icedtea-gcjwebplugin               <none>                 <none>                 (no description available)
ii  icedtea-netx:amd64                 1.6.2-3ubuntu1         amd64                  NetX - implementation of the Java Network Launching Protocol (JNLP)
ii  icedtea-netx-common                1.6.2-3ubuntu1         all                    NetX - implementation of the Java Network Launching Protocol (JNLP)
ii  icedtea-plugin                     1.6.2-3ubuntu1         all                    web browser plugin to execute Java applets (dependency package)
un  icedtea6-plugin                    <none>                 <none>                 (no description available)

```

It means I have '**icedtea-8-plugin**' correctly installed in my desktop, right?

---

### Post by ajgreeny on 2018-04-02
You have four icedtea-plugin packages installed; they are the four listed with lines starting with ii.

I am not sure these days what exactly the plugins are useful for as Java is used less and less in browsers as far as I'm aware.

---

### Post by sdbhabal on 2018-04-02
I required this plugin to access my firewall through browser.
If I have installed this plugin in my desktop, then why I am not able to see this plugin in my browser plugin list.
Please find attached screenshot of the same.

---

### Post by ajgreeny on 2018-04-02
I believe the java-plugin has now become useless in Firefox versions after 52 so you may be totally out of luck.

I do not know if this is a Linux only property of FF as I don't use anything other than Linux; perhaps it works in Windows?

---

### Post by sdbhabal on 2018-04-03
So, I was trying to access my firewall using browser, for that I needed this plugin to be integrated with browser.
For windows, I have firewall client software which works perfectly fine.

---

### Post by ajgreeny on 2018-04-03
Sorry but I can't help you any more as I am out of my depth completely when discussing Java plugins, which with Firefox at least seem rather pointless.

I am not sure about the position if using chromium or Chrome as I seldom use the former and have never used Chrome.

---

