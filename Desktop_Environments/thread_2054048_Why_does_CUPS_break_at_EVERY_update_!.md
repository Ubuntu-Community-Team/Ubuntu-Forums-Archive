---
title: "Why does CUPS break at EVERY update ?!?"
date: 2012-09-06
forum: Desktop Environments
---

### Post by dargaud on 2012-09-06
Argh ! I can't stand CUPS anymore. Every upgrade breaks it. And then the next upgrade fixes it without me ever understanding WTF is wrong with it. It's like my 5th call for help in 2 years on this forum.

This time the symptoms are: the 1st page after a reboot prints halfway and stays in the printer while the 'data incoming' LED blinks. Forever. The job status says "Pending [...] Unable to send data to printer."

Doing a service restart doesn't help. I have a huge error_log bug here's the short version:
```
$ grep -v -C 5 "^D \|^I " /var/log/cups/error_log 
D [06/Sep/2012:19:29:00 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients"
D [06/Sep/2012:19:29:00 +0200] cupsdMarkDirty(P-----)
D [06/Sep/2012:19:29:00 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [06/Sep/2012:19:29:00 +0200] cupsdRegisterPrinter(p=0x7fd0fa7ea150(Stylus-Photo-R1800))
D [06/Sep/2012:19:29:00 +0200] Updating TXT record for EPSON Stylus Photo R1800 @ penguin (_ipp._tcp)
E [06/Sep/2012:19:29:00 +0200] Failed to update TXT record for EPSON Stylus Photo R1800 @ penguin: -2
D [06/Sep/2012:19:29:00 +0200] Registering Avahi printer Stylus-Photo-R1800 with name "EPSON Stylus Photo R1800 @ penguin" and type "_ipp._tcp,_cups,_universal"
D [06/Sep/2012:19:29:00 +0200] Adding TXT record for EPSON Stylus Photo R1800 @ penguin (_ipp._tcp)
D [06/Sep/2012:19:29:00 +0200] Adding TXT record for EPSON Stylus Photo R1800 @ penguin (_cups._sub._ipp._tcp)
D [06/Sep/2012:19:29:00 +0200] Adding TXT record for EPSON Stylus Photo R1800 @ penguin (_universal._sub._ipp._tcp)
D [06/Sep/2012:19:29:00 +0200] cupsdMarkDirty(P-----)
--
D [06/Sep/2012:19:31:00 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [06/Sep/2012:19:31:00 +0200] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [06/Sep/2012:19:31:00 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [06/Sep/2012:19:31:00 +0200] cupsdCloseClient: 17
D [06/Sep/2012:19:31:00 +0200] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
E [06/Sep/2012:19:31:00 +0200] [Job 156] Unable to send data to printer.
D [06/Sep/2012:19:31:00 +0200] [Job 156] Set job-printer-state-message to "Unable to send data to printer.", current level=ERROR
D [06/Sep/2012:19:31:00 +0200] [Job 156] libusb write operation returned fffffffc.
D [06/Sep/2012:19:31:00 +0200] [Job 156] Sent 495616 bytes...
D [06/Sep/2012:19:31:00 +0200] cupsdMarkDirty(-----S)
D [06/Sep/2012:19:31:00 +0200] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
--
D [06/Sep/2012:19:31:00 +0200] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [06/Sep/2012:19:31:00 +0200] cupsdMarkDirty(P-----)
D [06/Sep/2012:19:31:00 +0200] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients, printing jobs, and dirty files"
D [06/Sep/2012:19:31:00 +0200] cupsdRegisterPrinter(p=0x7fd0fa7ea150(Stylus-Photo-R1800))
D [06/Sep/2012:19:31:00 +0200] Updating TXT record for EPSON Stylus Photo R1800 @ penguin (_ipp._tcp)
E [06/Sep/2012:19:31:00 +0200] Failed to update TXT record for EPSON Stylus Photo R1800 @ penguin: -2
D [06/Sep/2012:19:31:00 +0200] Registering Avahi printer Stylus-Photo-R1800 with name "EPSON Stylus Photo R1800 @ penguin" and type "_ipp._tcp,_cups,_universal"
D [06/Sep/2012:19:31:00 +0200] Adding TXT record for EPSON Stylus Photo R1800 @ penguin (_ipp._tcp)
D [06/Sep/2012:19:31:00 +0200] Adding TXT record for EPSON Stylus Photo R1800 @ penguin (_cups._sub._ipp._tcp)
D [06/Sep/2012:19:31:00 +0200] Adding TXT record for EPSON Stylus Photo R1800 @ penguin (_universal._sub._ipp._tcp)
D [06/Sep/2012:19:31:00 +0200] cupsdMarkDirty(P-----)

```

---

### Post by dargaud on 2012-09-07
No taker ?
Doing cups restart, reboot, printer on/off and/or driver reinstall doesn't do anything.
One thing I notice is that after the printer gets stuck in the middle of the 1st print, it disapears from lsusb !!!

Printer works fine from a direct USB device in a VirtualBox WinXP.

---

### Post by dargaud on 2012-09-08
Bump again. I've been at it several days and can't find anything useful on the 'net. If I remove the CUPS config and restart from scratch, I get this in the error_log:
```
W [08/Sep/2012:12:40:11 +0200] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'EPSON-Stylus_Photo_R1800-Gray..' already exists                                                                                            
W [08/Sep/2012:12:40:11 +0200] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'EPSON-Stylus_Photo_R1800-RGB..' already exists                                                                                             
W [08/Sep/2012:12:40:11 +0200] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-EPSON-Stylus_Photo_R1800' already exists                                                                                                
W [08/Sep/2012:12:40:22 +0200] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'EPSON-Stylus_Photo_R1800-Gray..' already exists
W [08/Sep/2012:12:40:22 +0200] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'EPSON-Stylus_Photo_R1800-RGB..' already exists
W [08/Sep/2012:12:40:22 +0200] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-EPSON-Stylus_Photo_R1800' already exists
W [08/Sep/2012:12:40:22 +0200] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'EPSON-Stylus_Photo_R1800-Gray..' already exists
W [08/Sep/2012:12:40:22 +0200] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'EPSON-Stylus_Photo_R1800-RGB..' already exists
W [08/Sep/2012:12:40:22 +0200] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-EPSON-Stylus_Photo_R1800' already exists

```
I wonder if there's some file somewhere that doesn't get removed...
```
$ locate freedesktop.Color
/etc/dbus-1/system.d/org.freedesktop.ColorManager.conf
/usr/share/dbus-1/interfaces/org.freedesktop.ColorManager.Device.xml
/usr/share/dbus-1/interfaces/org.freedesktop.ColorManager.Profile.xml
/usr/share/dbus-1/interfaces/org.freedesktop.ColorManager.Sensor.xml
/usr/share/dbus-1/interfaces/org.freedesktop.ColorManager.xml
/usr/share/dbus-1/system-services/org.freedesktop.ColorManager.service

```

---

### Post by dargaud on 2012-09-08
Here's some more info from the syslog file:
```
kernel: [66275.040632] usblp0: removed
kernel: [66275.053294] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04B8 pid 0x0007
udev-configure-printer: add /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/usb/lp0
udev-configure-printer: device devpath is /devices/pci0000:00/0000:00:12.2/usb1/1-1
udev-configure-printer: Device already handled
kernel: [66287.352465] usblp0: removed
kernel: [66303.069647] ehci_hcd 0000:00:12.2: force halt; handshake ffffc90000c1c824 00004000 00000000 -> -110
kernel: [66303.069659] ehci_hcd 0000:00:12.2: HC died; cleaning up
kernel: [66303.069678] cannot submit datapipe for urb 1, error -19: no device
kernel: [66303.069726] usb 1-1: USB disconnect, device number 2
kernel: [66303.072869] usb 1-3: USB disconnect, device number 4
udev-configure-printer: remove /devices/pci0000:00/0000:00:12.2/usb1/1-1
udev-configure-printer: URI of print queue: usb://EPSON/Stylus%20Photo%20R1800?serial=RS0070507301426530, normalized: epson stylus photo r1800 serial rs0070507301426530
udev-configure-printer: URI of detected printer: usb://EPSON/Stylus%20Photo%20R1800?serial=RS0070507301426530, normalized: epson stylus photo r1800 serial rs0070507301426530
udev-configure-printer: Queue ipp://localhost:631/printers/EPSON_Stylus_Photo_R1800 has matching device URI
udev-configure-printer: Disabled printer ipp://localhost:631/printers/EPSON_Stylus_Photo_R1800 as the corresponding device was unplugged or turned off
kernel: [66304.072380] timeout: still 1 active urbs..

```

---

### Post by dargaud on 2012-09-08
Solved ?
I did a simple 'aptitude reinstall cups', deleted and reinstalled the printer and now it works. Go figure...

---

### Post by kw217 on 2012-09-22
Thanks, the reinstall helped my Canon MX300 on Ubuntu 12.04 as well. I had to pick a different name for the printer when I reinstalled though - using the same name meant I still got problems.

--KW 8-)

---

### Post by Artif on 2012-11-17
> **dargaud said:**
> Solved ?
I did a simple 'aptitude reinstall cups', deleted and reinstalled the printer and now it works. Go figure...

 Why break at EVERY update? It seems this is a question. Historico-philosophical. Linux and opensource software are permanently floating and unstable. Developers and apologists are sometimes young (no life experience), some times extremely creative persons (huge unstableness). Now days. 

CUPS: 

Solved? It seems not solved. You just reinstalled CUPS, I reinstalled drivers (one more time, average is 1 per mounth since spring), and it will be workable for some time. Until smth. unknown will happens... Can't catch. May be VNC session related???? 

It seems it do not depend on drivers. I tried both - third party and &quot;official&quot; - drivers with the same result. The similar problem descriptions could be found for another printers. In one e-mail can be found: it may be related not to Apple, but to opensource community code, have been commited some mounth ago to cups.org, as far as I remeber the URL. 


Excuse me, please, for some arraignment and sharp rhetoric.

---

### Post by TiberiusT on 2012-11-17
> **Artif said:**
> I reinstalled drivers (one more time, average is 1 per mounth since spring), and it will be workable for some time. Until smth. unknown will happens... Can't catch. May be VNC session related???? 


Thanks Dargaud for bringing this up. I echo your first para in the 1st post :( . @Artif - that quote above is dittoed here. CUPS and network printing (I use IPP) is the only unreliable part of my home network. It is indeed about monthly that one user cannot print, and either a client delete/reinstall of the printer and driver, or a server reboot, is required. It doesn't take long, but if I'm not at home....no printing.

I haven't bothered looking into it, kinda keep hoping some upgrade will silently fix something, but it's been like this forever (18 months since I switched from Win). It's a major pain in the derriere...

Bah!
T

---

### Post by mark bower on 2012-11-18
the unexpected/recurring problems with each Ubuntu update surely causes some to abandon Ubuntu, if not linux.

CUPS worked just perfectly for me with 10.10 and a print server on my HP Laserjet4 Plus.  But after installing 12.04, CUPS would not find the print server.  Per forum suggestion, I installed CUPS via the web.  There is still a v. minor problem in that an error msg is generated midstream printing, but then a final printed o.k. msg pops up and the print is complete.

I am also no fan of Unity and "restored" my desktop with Gnome-classic.  While loyal, I keep Mint Linux in mind and have already played with it a bit.

mark bower

---

### Post by Al Stat on 2012-11-30
I found one bug report:
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/997040](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/997040)

In a short: after a reboot do
```
sudo rmmod usblp
```and try to print.

If it was helpful, the module can be blacklisted in "/etc/modprobe.d/blacklist.conf".

There is a command to add a printer, instead of navigating through [http://...:631](http://...:631) GUI:
```

lpinfo -m | grep "your printer model part or index or else" # Will show a PPD file name; like 'HP-LaserJet_1020.ppd.gz'
lpadmin -p test_prn -E -v "usb://HP/LaserJet%201020?serial=XXXXXXX" -m HP-LaserJet_1020.ppd.gz
```I have a script for "printing hard reset". It allows me in a single click reset all this painful staff. But be aware: the script is highly Ubuntu and version centric, created with a pain printer HP LJ 1020 in mind, seems to be specific to my installed packages list. It should NOT be used until you understand in details every action to be performed by the script.
```

#!/bin/bash

#
#  Copyright 2012 Al Stat at UbuntuForums.Org
#
#  This file is part of PHR - Printing Hard Resetter.
#
#  PHR is free software: you can redistribute it and/or modify
#  it under the terms of the GNU General Public License as published by
#  the Free Software Foundation, either version 3 of the License, or
#  (at your option) any later version.
#
#  PHR is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#  GNU General Public License for more details.
#
#  You should have received a copy of the GNU General Public License
#  along with PHR.  If not, see <http://www.gnu.org/licenses/>.
#
##

#
#  This cript intended to assist in wars between Foo2Zjs and HP.
#  It will reinstall CUPS and some drivers for ZjsStream painfull printers.
#
#  It is DR - quick and dirty. It is bounded to concrete packages managment
#  system - Apt, concrete OS - Ubuntu, and concrete painfull printer. You shoud
#  NOT rely on it, if you in details do not understand actions to be perfomed
#  by PHR.
#
#  However, it is easy to adopt this script for your unique needs.
#
#  This script may be launched as root by ordinary user, in case of proper
#  sudoers policy. Pay attention - source code and firmware source must not
#  accessible for a user. You must have third user account for compilation of
#  the sources and a storage of firmware, or compile it as root. Build as root
#  is highly NOT recommended. Use and substitude in corresponding places
#  'su -l ... -c ...'.
#
##

declare -ra ruinedCUPSPackagesNamesArray=(\
                                    "cups" \
                                    "cups-driver-gutenprint" \
                                    "cups-pdf" \
                                    "printer-driver-gutenprint" \
                                    )

declare -ra ruinedFoo2ZjsPackagesNamesArray=(\
                                    "foo2zjs" \
                                    "hannah-foo2zjs" \
                                    "printer-driver-foo2zjs" \
                                    )

declare -ra dirsToBeErasedArray=(
                        "/usr/share/foo2zjs" \
                        "/usr/share/foo2qpdl/crd" \
                        "/lib/firmware/hp" \
                        "/usr/share/doc/foo2zjs" \
                        )

declare -r  urlOfDrivers="http://foo2zjs.rkkda.com"
declare -r  dirWorking="$( pwd )"
declare -r  fileWithPackagedSourceREMOTE="${urlOfDrivers}/foo2zjs.tar.gz"
declare     dirUnpackedSource=""
declare -r  filePackageWithDriversLOCAL="${dirWorking}/foo2zjs.tar.gz"

declare -r  firmwareId="1020"
declare -r  fileWithPACKEDFirmwareShortName="sihp${firmwareId}.tar.gz"
#declare -r  fileWithFirmware="sihp1020.img"
declare -r  filesWithFirmwareNameTemplate="sihp${firmwareId}*"
declare -r  fileExeFirmwareDownloaderShortName="getweb"

function requestUserAgreement {
    local -r messageText="${@}"
    
    local userFeedback=""

    echo -ne "\n"
    echo "${messageText}" "[Yes/no]"
    read userFeedback
    [ "${userFeedback,,}" == "yes" ] \
        || [ "${userFeedback,,}" == "y" ] \
        && return 0
    echo "Got negative answer. Bailing out." >&2
    exit ${?}
}

function downloadPackagedSource {
    local -r objectDonor="${1}"
    local -r fileAcceptor="${2}"

    [ -f "${fileAcceptor}" ] \
        && reportThat "INFORMATION:${0}:${LINENO}: Will skip download as already have file named '${fileAcceptor}'." >&2 \
        && return 0
    wget -O "${fileAcceptor}" "${objectDonor}" \
        ; isDoneWithError "${LINENO}"
    return ${?}
}

function isDoneWithError {
    local -r obtainedByLuckyStrikeErrorCode="${?}" # Must be the first line - the first strike.
    #local -r obtainedErrorCode="${1}" # XXX - it is not evident, it is so in all possible realisations.

    local -r  thisInstanceCallLineNumber="${1}"

    local -ri codeToBeSuccess=0
    local     lineNumberForOutput=""

    lineNumberForOutput="${LINENO}"
    [ -n "thisInstanceCallLineNumber" ] \
        && lineNumberForOutput="${thisInstanceCallLineNumber}"

    [ "${obtainedByLuckyStrikeErrorCode}" == "${codeToBeSuccess}" ] \
        && return ${codeToBeSuccess}

    echo "ERROR:${0}:${lineNumberForOutput}: Got feedback with error code '${obtainedByLuckyStrikeErrorCode}'. Bailing out." >&2
    exit ${obtainedByLuckyStrikeErrorCode}
    
}

function reportThat {
    local messageText="${1}"
    #echo -ne "\n"
    echo "${messageText}"
} >&2

function downloadFirmware {
    local -r dirAcceptorAndCodeHolder="${1}"
    local -r firmwareToBeObtainedId="${2}"

    local -r downloaderExe="${dirAcceptorAndCodeHolder}/${fileExeFirmwareDownloaderShortName}"
    local -r fileWithFirmwareNameTemplate="${dirAcceptorAndCodeHolder}/${filesWithFirmwareNameTemplate}"
    local    foundFile=""

    [ -d "${dirAcceptorAndCodeHolder}" ] \
        ; isDoneWithError "${LINENO}"
    [ -x "${downloaderExe}" ] \
        ; isDoneWithError "${LINENO}"

    isAlreadyExist "${fileWithFirmwareNameTemplate}" \
        && echo "INFORMATION:${0}:${LINENO}: Will skip download as already have a file '${fileWithFirmwareNameTemplate}'." >&2 \
        && return 0

    "${downloaderExe}" "${firmwareToBeObtainedId}" \
        ; isDoneWithError "${LINENO}"
    return ${?}
}

function isAlreadyExist {
    local -r targetNameTemplate="${1}"

    local foundFile=""

    foundFile="$( find "$( dirname "${fileWithFirmwareNameTemplate}" )" \
        -name "$( basename "${fileWithFirmwareNameTemplate}" )" )"

    [ -n "${foundFile}" ] \
        && return 0
    return 1
}

function evaluateSubDirForUnpackedSource {
    local packageWithFiles="${1}"
    local firstFileNameInPackage=""
    local sourceAcceptorDirectory=""

    [ ! -f "${packageWithFiles}" ] \
        && isDoneWithError "${LINENO}"

    shopt -s extglob
    read firstFileNameInPackage <<< "$( tar tf "${packageWithFiles}" )"
    sourceAcceptorDirectory="${firstFileNameInPackage/\/*/}"

    echo "${sourceAcceptorDirectory}"
}




  #
 # #
# # #
 # #
  #



  
reportThat "INFORMATION:${0}:${LINENO}: Start. $( date ) See details at <${urlOfDrivers}>."
reportThat "INFORMATION:${0}:${LINENO}: Packages to be affected explicitly: ${ruinedCUPSPackagesNamesArray
[*]}."
reportThat "INFORMATION:${0}:${LINENO}: Directories to be erased explicitly: ${dirsToBeErasedArray
[*]}."
reportThat "INFORMATION:${0}:${LINENO}: You must have to be already installed development tools."
requestUserAgreement "Are you shure you want to continue?"

reportThat "INFORMATION:${0}:${LINENO}: Downloading Foo2Zjs driver. If not already have file '${filePackageWithDriversLOCAL}'."
downloadPackagedSource "${fileWithPackagedSourceREMOTE}" "${filePackageWithDriversLOCAL}" \
    ; isDoneWithError "${LINENO}"

requestUserAgreement "Packages and directories removing needs super user privileges. Are you shure you want to enter super user password later?"
sudo true \
    ; isDoneWithError "${LINENO}"

reportThat "INFORMATION:${0}:${LINENO}: Doing, in terms of apt-get, 'remove' and 'install' packages related to CUPS itself."
sudo apt-get remove "${ruinedCUPSPackagesNamesArray[@]}" \
    ; isDoneWithError "${LINENO}"
sudo apt-get install "${ruinedCUPSPackagesNamesArray[@]}" \
    ; isDoneWithError "${LINENO}"

reportThat "INFORMATION:${0}:${LINENO}: Doing, in terms of apt-get, 'purge' Foo2Zjs printer drivers."
sudo apt-get purge "${ruinedFoo2ZjsPackagesNamesArray[@]}" \
    ; isDoneWithError "${LINENO}"
sudo rm -rf "${dirsToBeErasedArray[@]}" \
    ; isDoneWithError "${LINENO}"
sudo -K

reportThat "INFORMATION:${0}:${LINENO}: Unpacking and compiling."


dirUnpackedSource="${dirWorking}/$( evaluateSubDirForUnpackedSource "${filePackageWithDriversLOCAL}" )"
mkdir -p "${dirUnpackedSource}" \
    ; isDoneWithError "${LINENO}"

# --directory "$( dirname "${dirUnpackedSource}" )"
tar zxf "${filePackageWithDriversLOCAL}" \
    ; isDoneWithError "${LINENO}"

pushd . >/dev/null
cd "${dirUnpackedSource}" \
    ; isDoneWithError "${LINENO}"
make \
    ; isDoneWithError "${LINENO}"

reportThat "INFORMATION:${0}:${LINENO}: Downloading firmware. If not already have in '${dirUnpackedSource}' file '${filesWithFirmwareNameTemplate}'."
downloadFirmware "${dirUnpackedSource}" "${firmwareId}" \
    ; isDoneWithError "${LINENO}"

requestUserAgreement "UNinstallation by 'make' job and subsecuent installation, both, needs super user access. Are you shure you want to enter super user password later?"
sudo true \
    ; isDoneWithError "${LINENO}"

reportThat "INFORMATION:${0}:${LINENO}: UNinstalling."
sudo make uninstall \
    ; isDoneWithError "${LINENO}"
reportThat "INFORMATION:${0}:${LINENO}: Installing."
sudo make install \
    ; isDoneWithError "${LINENO}"
requestUserAgreement "You do not need 'hotplug' for every printer model. You may read about 'hotplug' on <${urlOfDrivers}>. Or in file '${dirUnpackedSource}/INSTALL'.     Install 'hotplug'?" \
    && sudo make install-hotplug \
    || isDoneWithError "${LINENO}"

reportThat "INFORMATION:${0}:${LINENO}: Manipulating with CUPS."
sudo make cups \
    ; isDoneWithError "${LINENO}"
sudo -K

popd >/dev/null

reportThat "INFORMATION:${0}:${LINENO}: Done. $( date )"


```

---

### Post by Artif on 2012-12-04
.

---

### Post by Artif on 2012-12-04
This did the trick - [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/997040/comments/75](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/997040/comments/75)

See printers list,
See their names only,
Set up a wanted printer.
```

lpstat -p
lpstat -p | awk '{print $2}'
lpadmin -p <printer> -o usb-no-reattach-default=true

```

The last command will not make permanent changes. It may be placed in '/etc/rc.local', or ~/.config/autostart/*desktop'.

---

