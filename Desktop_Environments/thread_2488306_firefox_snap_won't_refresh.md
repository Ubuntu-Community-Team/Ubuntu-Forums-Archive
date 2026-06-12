---
title: "firefox snap won't refresh"
date: 2023-06-30
forum: Desktop Environments
---

### Post by rwigle on 2023-06-30
trying to refresh firefox 114.0.1 (64-bit) snap on Ubuntu Ubuntu 22.04.2 with "sudo snap refresh" gives:

error: cannot perform the following tasks:
- Fetch and check assertions for snap "firefox" (2800) (cannot verify snap "firefox", no matching signatures found)

Suggestions?

---

### Post by paulparker2 on 2023-06-30
Try viewing:  
> sudo snap info  firefox

---

### Post by rwigle on 2023-07-01
name:      firefox
summary:   Mozilla Firefox web browser
publisher: Mozilla&#10003;
store-url: [https://snapcraft.io/firefox](https://snapcraft.io/firefox)
contact:   [https://support.mozilla.org/kb/file-bug-report-or-feature-request-mozilla](https://support.mozilla.org/kb/file-bug-report-or-feature-request-mozilla)
license:   unset
description: |
  Firefox is a powerful, extensible web browser with support for modern web application
  technologies.
commands:
  - firefox
  - firefox.geckodriver
snap-id:      3wdHCAVyZEmYsCMFDE9qt92UV8rC8Wdk
tracking:     latest/stable
refresh-date: 16 days ago, at 17:02 EDT
channels:
  latest/stable:    114.0.2-1     2023-06-20 (2800) 256MB -
  latest/candidate: 115.0-2       2023-06-29 (2846) 256MB -
  latest/beta:      115.0b9-1     2023-06-23 (2825) 256MB -
  latest/edge:      116.0a1       2023-06-30 (2848) 284MB -
  esr/stable:       102.12.0esr-1 2023-06-06 (2735) 186MB -
  esr/candidate:    102.13.0esr-1 2023-06-29 (2842) 186MB -
  esr/beta:         &#8593;                                     
  esr/edge:         &#8593;                                     
installed:          114.0.1-1                (2760) 256MB -

---

