---
title: "Unity8 Installation error"
date: 2015-04-26
forum: Desktop Environments
---

### Post by slooksterpsv on 2015-04-26
It always gives this error, I tried the proposed packages, but those weren't any help either. When running click it gives that error as well. I'm not sure what else to try - all updates and all upgrades:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
25 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
[b]Setting up click (0.4.38.5) ...
Traceback (most recent call last):
  File "/usr/bin/click", line 31, in <module>
    from click import commands
ImportError: cannot import name 'commands'[/b]
dpkg: error processing package click (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libunity-scopes3:amd64 (0.6.16+15.04.20150410.3-0ubuntu1) ...
Traceback (most recent call last):
  File "/usr/bin/click", line 31, in <module>
    from click import commands
ImportError: cannot import name 'commands'
dpkg: error processing package libunity-scopes3:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of unity-plugin-scopes:amd64:
 unity-plugin-scopes:amd64 depends on libunity-scopes3 (>= 0.6.16+15.04.20150410.1); however:
  Package libunity-scopes3:amd64 is not configured yet.

dpkg: error processing package unity-plugin-scopes:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity8-common:
 unity8-common depends on unity-plugin-scopes | unity-scopes-impl; however:
  Package unity-plugin-scopes:amd64 is not configured yet.
  Package unity-scopes-impl is not installed.
  Package unity-plugin-scopes:amd64 which provides unity-scopes-impl is not configured yet.
 unity8-common depends on unity-scopes-impl-6; however:
  Package unity-scopes-impl-6 is not installed.
  Package unity-plugin-scopes:amd64 which provides unity-scopes-impl-6 is not configured yet.

dpkg: error processing package unity8-common (--configure):
 dependency problems - leaving unconfigured
Setting up pay-service (2.0.0+14.10.20140916-0ubuntu1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because MaxReports is reached already
        Traceback (most recent call last):
  File "/usr/bin/click", line 31, in <module>
    from click import commands
ImportError: cannot import name 'commands'
dpkg: error processing package pay-service (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of unity8-private:amd64:
 unity8-private:amd64 depends on pay-service; however:
  Package pay-service is not configured yet.

dpkg: error processing package unity8-private:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-system-settings:
 ubuntu-system-settings depends on click; however:
  Package click is not configured yet.

dpkg: error processing package ubuntu-system-settings (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity8:No apport report written because MaxReports is reached already
                                        No apport report written because MaxReports is reached already
                      No apport report written because MaxReports is reached already

 unity8 depends on ubuntu-system-settings; however:
  Package ubuntu-system-settings is not configured yet.
 unity8 depends on unity-launcher-impl-4; however:
  Package unity-launcher-impl-4 is not installed.
  Package unity8-private:amd64 which provides unity-launcher-impl-4 is not configured yet.
 unity8 depends on unity8-common (= 8.02+15.04.20150409.1-0ubuntu1); however:
  Package unity8-common is not configured yet.
 unity8 depends on unity8-private (= 8.02+15.04.20150409.1-0ubuntu1); however:
  Package unity8-private:amd64 is not configured yet.

dpkg: error processing package unity8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-network:
 indicator-network depends on unity8 (>= 8.00+14.10.20140806); however:
  Package unity8 is not configured yet.
No apport report written because MaxReports is reached already

dpkg: error processing package indicator-network (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-system-settings-online-accounts:No apport report written because MaxReports is reached already

 ubuntu-system-settings-online-accounts depends on ubuntu-system-settings; however:
  Package ubuntu-system-settings is not configured yet.

dpkg: error processing package ubuntu-system-settings-online-accounts (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of account-plugin-ubuntuone:No apport report written because MaxReports is reached already

 account-plugin-ubuntuone depends on ubuntu-system-settings-online-accounts; however:
  Package ubuntu-system-settings-online-accounts is not configured yet.

dpkg: error processing package account-plugin-ubuntuone (--configure):
 dependency problems - leaving unconfigured
Setting up click-apparmor (0.3.8) ...No apport report written because MaxReports is reached already

Traceback (most recent call last):
  File "/usr/bin/click", line 31, in <module>
    from click import commands
ImportError: cannot import name 'commands'
dpkg: error processing package click-apparmor (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libunity-scopes-dev:amd64:
 libunity-scopes-dev:amd64 depends on libunity-scopes3 (= 0.6.16+15.04.20150410.3-0ubuntu1); however:
  Package libunity-scopes3:amd64 is not configured yet.

dpkg: error processing package libunity-scopes-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity-scope-tool:
 unity-scope-tool depends on unity8-common (= 8.02+15.04.20150409.1-0ubuntu1); however:
  Package unity8-common is not configured yet.
 unity-scope-tool depends on unity8-private (= 8.02+15.04.20150409.1-0ubuntu1); however:
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                              Package unity8-private:amd64 is not configured yet.
 unity-scope-tool depends on libunity-scopes-dev; however:
  Package libunity-scopes-dev:amd64 is not configured yet.

dpkg: error processing package unity-scope-tool (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phablet-tools:
 phablet-tools depends on click; however:
  Package click is not configured yet.

dpkg: error processing package phablet-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qtcreator-plugin-ubuntu:No apport report written because MaxReports is reached already
                                                         No apport report written because MaxReports is reached already

 qtcreator-plugin-ubuntu depends on click; however:
  Package click is not configured yet.
 qtcreator-plugin-ubuntu depends on click-apparmor; however:
  Package click-apparmor is not configured yet.
 qtcreator-plugin-ubuntu depends on unity-scope-tool; however:
  Package unity-scope-tool is not configured yet.
 qtcreator-plugin-ubuntu depends on phablet-tools; however:
  Package phablet-tools is not configured yet.

dpkg: error processing package qtcreator-plugin-ubuntu (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntu-app-launch:
 ubuntu-app-launch depends on click-apparmor; however:
  Package click-apparmor is not configured yet.

dpkg: error processing package ubuntu-app-launch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-app-launch-tools:No apport report written because MaxReports is reached already

 ubuntu-app-launch-tools depends on ubuntu-app-launch (= 0.4+15.04.20150410-0ubuntu1); however:
  Package ubuntu-app-launch is not configured yet.

dpkg: error processing package ubuntu-app-launch-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-sdk-libs-dev:amd64:No apport report written because MaxReports is reached already

 ubuntu-sdk-libs-dev:amd64 depends on libunity-scopes-dev; however:
  Package libunity-scopes-dev:amd64 is not configured yet.

dpkg: error processing package ubuntu-sdk-libs-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-sdk:No apport report written because MaxReports is reached already

 ubuntu-sdk depends on ubuntu-sdk-libs-dev; however:
  Package ubuntu-sdk-libs-dev:amd64 is not configured yet.
 ubuntu-sdk depends on phablet-tools; however:
  Package phablet-tools is not configured yet.
 ubuntu-sdk depends on qtcreator-plugin-ubuntu; however:
  Package qtcreator-plugin-ubuntu is not configured yet.

dpkg: error processing package ubuntu-sdk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity-scope-click:No apport report written because MaxReports is reached already

 unity-scope-click depends on account-plugin-ubuntuone; however:
  Package account-plugin-ubuntuone is not configured yet.
 unity-scope-click depends on pay-service; however:
  Package pay-service is not configured yet.
 unity-scope-click depends on ubuntu-app-launch-tools; however:
  Package ubuntu-app-launch-tools is not configured yet.
 unity-scope-click depends on libunity-scopes3 (>= 0.6.15+15.04.20150407); however:
  Package libunity-scopes3:amd64 is not configured yet.

dpkg: error processing package unity-scope-click (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity-scope-mediascanner2:No apport report written because MaxReports is reached already

 unity-scope-mediascanner2 depends on libunity-scopes3 (>= 0.6.15+15.04.20150407); however:
  Package libunity-scopes3:amd64 is not configured yet.

dpkg: error processing package unity-scope-mediascanner2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity-scope-scopes:No apport report written because MaxReports is reached already

 unity-scope-scopes depends on libunity-scopes3 (>= 0.6.0+14.10.20140804.1); however:
  Package libunity-scopes3:amd64 is not configured yet.

dpkg: error processing package unity-scope-scopes (--configure):
 dependency problems - leaving unconfigured
Setting up url-dispatcher:amd64 (0.1+15.04.20150123-0ubuntu1) ...No apport report written because MaxReports is reached already

Traceback (most recent call last):
  File "/usr/bin/click", line 31, in <module>
    from click import commands
ImportError: cannot import name 'commands'
dpkg: error processing package url-dispatcher:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of unity8-desktop-session-mir:
 unity8-desktop-session-mir depends on unity8; however:
  Package unity8 is not configured yet.
 unity8-desktop-session-mir depends on ubuntu-app-launch; however:
  Package ubuntu-app-launch is not configured yet.
 unity8-desktop-session-mir depends on url-dispatcher; however:
  Package url-dispatcher:amd64 is not configured yet.

dpkg: error processing package unity8-desktop-session-mir (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 click
 libunity-scopes3:amd64
 unity-plugin-scopes:amd64
 unity8-common
 pay-service
 unity8-private:amd64
 ubuntu-system-settings
 unity8
 indicator-network
 ubuntu-system-settings-online-accounts
 account-plugin-ubuntuone
 click-apparmor
 libunity-scopes-dev:amd64
 unity-scope-tool
 phablet-tools
 qtcreator-plugin-ubuntu
 ubuntu-app-launch
 ubuntu-app-launch-tools
 ubuntu-sdk-libs-dev:amd64
 ubuntu-sdk
 unity-scope-click
 unity-scope-mediascanner2
 unity-scope-scopes
 url-dispatcher:amd64
 unity8-desktop-session-mir
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by grahammechanical on 2015-04-27
How did you install Unity8? There are 3 ways to run Unity8

1) Install Unity 8 in LXC

[https://wiki.ubuntu.com/Unity8inLXC](https://wiki.ubuntu.com/Unity8inLXC)

2) Download and install the Ubuntu Desktop Next ISO image

[https://wiki.ubuntu.com/Unity8DesktopIso](https://wiki.ubuntu.com/Unity8DesktopIso)

Or

3) install unity8-desktop-session-mir

[https://wiki.ubuntu.com/Unity8Desktop](https://wiki.ubuntu.com/Unity8Desktop)

There are Unity8 packages in the archives. If we install them separately then we may get dependency problems like these.

Regards.

---

