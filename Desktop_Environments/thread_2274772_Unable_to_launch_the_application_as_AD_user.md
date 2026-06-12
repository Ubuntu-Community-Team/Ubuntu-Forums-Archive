---
title: "Unable to launch the application as AD user"
date: 2015-04-22
forum: Desktop Environments
---

### Post by gopukrishnan on 2015-04-22
Hi,

I have followed the below link and setup AD authentication for my machine :

```
http://tweaktheserver.com/integrate-linux-machine-with-ad/
```

Everything is working fine as expected and users can login using their AD credentials.

I have installed kingsoft in Lubuntu 14.04 and not able to start the application by clicking on the software shortcut available. When I click on the application, nothing happens and no error I am getting. 

```
vi /usr/share/applications/wps-office-wpp.desktop

[Desktop Entry]
Comment=Use Kingsoft Presentation to edit and play presentations.
Comment[zh_CN]=ä½¿ç¨ WPS æ¼ç¤ºç¼è¾ãæ*æ¾æ¼ç¤ºæç¨¿
Exec=/usr/bin/wpp %f
GenericName=Kingsoft Presentation
GenericName[zh_CN]=WPS æ¼ç¤º
MimeType=application/wps-office.dps;application/wps-office.dpt;application/wps-office.ppt;application/wps-office.pot;application/vnd.ms-powerpoint;application/vnd.mspowerpoint;application/mspowerpoint;application/powerpoint;application/x-mspowerpoint;application/wps-office.pptx;application/wps-office.potx;
Name=Kingsoft Presentation
Name[zh_CN]=WPS æ¼ç¤º
StartupNotify=false
Terminal=false
Type=Application
Categories=Office;Presentation;Qt;
X-DBUS-ServiceName=
X-DBUS-StartupType=
X-KDE-SubstituteUID=false
X-KDE-Username=
Icon=wps-office-wppmain
InitialPreference=3
```

So I have tried to run the application manually from command prompt as ```
/usr/bin/wps
``` but getting the below error :

```
domain.com\user.name@hostname18:~$ /usr/bin/wps
QGtkStyle could not resolve GTK. Make sure you have installed the proper libraries.
/usr/bin/wps: line 31:  5996 Segmentation fault      (core dumped) ${gInstallPath}/office6/${gApp} ${gOpt} "$@"
/usr/bin/wps_error_check.sh: line 16: readelf: command not found
```

Content of wps:

```

#!/bin/bash

gOpt=
gTemplateExt=("wpt" "dot" "dotx")
gBinPath=$(dirname "$0")
if [ -d "${gBinPath}/office6" ]; then
        gInstallPath=${gBinPath}
else
        gInstallPath=/opt/kingsoft/wps-office
fi
gApp=wps



function parse_arg()
{
        if [ $# -eq 1 ] ; then
                ext="${1##*.}"
                if [ "" = "${ext}" ] ; then
                        return 0
                fi

                for i in ${gTemplateExt}
                do
                        if [ "${ext}" = "${i}" ] ; then
                                gOpt=-t
                        fi
                done
        fi
}

function run()
{
        oldPwd="${PWD}"
        if [ -e "${gInstallPath}/office6/${gApp}" ] ; then
                if [ -d /usr/lib32/gtk-2.0 ]; then
                        export GTK_PATH=/usr/lib32/gtk-2.0
                fi
                ${gInstallPath}/office6/${gApp} ${gOpt} "$@" || ${gBinPath}/wps_error_check.sh ${gInstallPath}/office6/${gApp}
        else
                echo "${gApp} does not exist!"
        fi
}

function main()
{
        parse_arg "$@"
        run "$@"
}

main "$@"

```


Permission of wps :

```
-rwsr-xr-x 1 root root 792 Aug 16  2013 /usr/bin/wps*
```

```
root@hostname18:/usr/share/applications# ll /opt/kingsoft/wps-office/
total 16
drwxr-xr-x  4 root root 4096 Apr 20 15:50 ./
drwxr-xr-x  3 root root 4096 Apr 20 15:49 ../
drwxr-xr-x 13 root root 4096 Apr 20 15:50 office6/
drwxr-xr-x  2 root root 4096 Apr 20 15:50 utility/
```




Running the same command as the local user in the machine just works fine.

---

### Post by dino99 on 2015-04-22
the error you get:  QGtkStyle could not resolve GTK. Make sure you have installed the proper libraries.

so either some are missed, or their version mismatch

---

### Post by gopukrishnan on 2015-04-23
Hi[**[COLOR=#000000] dino99[/COLOR]**]("http://ubuntuforums.org/member.php?u=129712") 	 

Actually I am able to run the same command as root user and start the application. Is there any way this library is not available for the AD users ?

---

### Post by dino99 on 2015-04-23
> **gopukrishnan said:**
> Hi[**[COLOR=#000000] dino99[/COLOR]**]("http://ubuntuforums.org/member.php?u=129712") 	 

Actually I am able to run the same command as root user and start the application. Is there any way this library is not available for the AD users ?

oh, then a chmod +x package_name might help to run without being root :p  (replace with the real name indeed)

---

### Post by gopukrishnan on 2015-04-24
Hello [**[COLOR=#000000]dino99[/COLOR]**]("http://ubuntuforums.org/member.php?u=129712"),

I hope you read my first post. It is already having execute permission.


```
-rwsr-xr-x 1 root root 792 Aug 16  2013 /usr/bin/wps*
```

---

### Post by gopukrishnan on 2015-04-29
Any other suggestions ?

---

### Post by mprem on 2015-07-17
@gopukrishnan Did you find any solution for this? Stuck up with the same issue on installing WPS office on Fedora 22

---

