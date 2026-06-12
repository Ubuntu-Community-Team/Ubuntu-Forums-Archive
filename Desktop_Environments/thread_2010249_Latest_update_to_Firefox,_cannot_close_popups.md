---
title: "Latest update to Firefox, cannot close popups"
date: 2012-06-25
forum: Desktop Environments
---

### Post by lister171254 on 2012-06-25
After the latest automatic update to Firefox, I cannot close any of the popup windows (including the About Firefox window). There us no bar on the popup to minimize/close, the window on the popups; only on the main window

Given that the is an Ubuntu spevcif version, I'm posting this here rather than with mozilla.

Following is a copy of the troubleshooting info

  Application Basics

        Name
        Firefox

        Version
        13.0.1

        User Agent
        Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:13.0) Gecko/20100101 Firefox/13.0.1

        Profile Directory

          Open Directory

        Enabled Plugins

          about:plugins

        Build Configuration

          about:buildconfig

        Crash Reports

          about:crashes

        Memory Use

          about:memory

  Extensions

        Name

        Version

        Enabled

        ID

        Global Menu Bar integration
        3.2.3
        true
        [email]globalmenu@ubuntu.com[/email]

        Ubuntu Firefox Modifications
        1.0.4
        true
        [email]ubufox@ubuntu.com[/email]

  Important Modified Preferences

      Name

      Value

        browser.cache.disk.capacity
        1048576

        browser.cache.disk.smart_size.first_run
        false

        browser.cache.disk.smart_size_cached_value
        1048576

        browser.places.smartBookmarksVersion
        3

        browser.startup.homepage
        [http://www.bbc.co.uk/news/](http://www.bbc.co.uk/news/)

        browser.startup.homepage_override.buildID
        20120615085229

        browser.startup.homepage_override.mstone
        13.0.1

        dom.disable_window_move_resize
        true

        extensions.lastAppVersion
        13.0.1

        network.cookie.prefsMigrated
        true

        places.history.expiration.transient_current_max_pages
        104858

        privacy.donottrackheader.enabled
        true

        privacy.sanitize.migrateFx3Prefs
        true

  Graphics

        Adapter Description
        NVIDIA Corporation -- GeForce GTX 570/PCI/SSE2

        Vendor ID
        NVIDIA Corporation

        Device ID
        GeForce GTX 570/PCI/SSE2

        Driver Version
        4.1.0 NVIDIA 280.13

        WebGL Renderer
        NVIDIA Corporation -- GeForce GTX 570/PCI/SSE2 -- 4.1.0 NVIDIA 280.13

        GPU Accelerated Windows
        0

        AzureBackend
        skia

  JavaScript

        Incremental GC
        1

  Library Versions

        Expected minimum version

        Version in use

        NSPR
        4.9
        4.9

        NSS
        3.13.4.0 Basic ECC
        3.13.4.0 Basic ECC

        NSS Util
        3.13.4.0
        3.13.4.0

        NSS SSL
        3.13.4.0 Basic ECC
        3.13.4.0 Basic ECC

        NSS S/MIME
        3.13.4.0 Basic ECC
        3.13.4.0 Basic ECC

---

### Post by lister171254 on 2012-06-26
Hmmm, I think it's a commbiz problem as the top panel on other windows is also missing.

---

### Post by Andrew_P on 2012-06-26
If you think you have problems, Firefox 13.0.1 on Ubuntu 10.04.4 is now totally hosed.  I can't get it to stay up for more than a few minutes at at time.  It's constantly crashing with segmentation faults in libpthread-2.11.1.so, frequently even as it's trying to recover from the previous crash.  Sometimes it appears to be restarting, but the GUI never comes up, and I find it is hung with futex_wait_queue_me in the waiting channel; the latter hangs never get reported to the Mozilla team, so they're sitting there fat, dumb and happy, deluding themselves that they've turned out a great product.  SeaMonkey 2.x and Thunderbird for Linux have the same problem. I trace SeaMonkey's issues to the moment that the team decided to adopt the Firefox code base.  It has gotten so bad in recent months that I'm ready to chuck all Mozilla products. :(  At least Opera still works reliably when a Mozilla program hasn't caused memory corruption to make it, or the entire system, crash.

(SeaMonkey crashed no less than 25 times in the period that I wrote the above paragraph, including 3-4 futex_wait_queue_me hangs during restart, requiring it to be killed with System Monitor.  I had Opera running, and it managed to crash it, too.) :(

It would be easy to blame my system, but no other programs on my Ubuntu box cause such problems.  They all will run for days without a hitch, as long as a Mozilla program doesn't have a memory segmentation fault that brings them down.

---

### Post by Oldhacker on 2012-07-21
I have been experiencing the same condition when in YouTube. When I attempt to go to another YouTube video, the Popup not only appears telling me that I have been selected to be a winner of something, but it won't let you leave. I've tried clicking  on the "x" in the upper right corner, or clicking on either option button in the popup with the same result: It takes you to another popup window. You can't exit YouTube either. The only way to escape is to close down Firefox from the Dash Icon on the side of the screen.

I tried YouTube in Chromium and there is no problem.
If this can't be rectified soon, good bye Firefox.

---

