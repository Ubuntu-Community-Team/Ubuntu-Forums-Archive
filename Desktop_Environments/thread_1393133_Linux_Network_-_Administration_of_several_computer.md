---
title: "Linux Network - Administration of several computers"
date: 2010-01-29
forum: Desktop Environments
---

### Post by eric_1982 on 2010-01-29
I have not messed with managing Linux computers in a corporate environment. I am however, very familiar with windows administration tools such as WSUS, Group Policy, Active Dir..etc. Are there similar tools available to help manage several Linux computers, basically tools used to help administrate a linux enviroment? I would like to be able to define what updates can be pushed out, lock down specific things, example apply a business background, map network drives..etc. Can any one supply me some names of some of these tools ect. Any information you can provide would be greatly appreciated! Thanks!!

---

### Post by eric_1982 on 2010-02-03
bump

---

### Post by pkm4o93 on 2010-02-03
I am interested in this too.  You mention many related items - you need to investigate LDAP.  I think apt-proxy or apt-cache will be involved also.  It appears autoyast is used by novell,so perhaps googling that will reveal something.  [https://lists.ubuntu.com/archives/ubuntu-users/2006-January/062807.html](https://lists.ubuntu.com/archives/ubuntu-users/2006-January/062807.html) [http://www.thelazysysadmin.net/2009/06/opensuse-autoyast-autoinstall-howto-part-1/](http://www.thelazysysadmin.net/2009/06/opensuse-autoyast-autoinstall-howto-part-1/)  As for 'group policy',patch management and locking down boxes im struggling to find info.  EDIT: Found some more.  2.7.5. Automatic download and upgrade of packages [http://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_automatic_download_and_upgrade_of_packages](http://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_automatic_download_and_upgrade_of_packages) 2.7.11. Proxy server for APT [http://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_proxy_server_for_apt](http://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_proxy_server_for_apt)

---

### Post by paalfe on 2010-09-05
Start reading:

[http://brainstorm.ubuntu.com/idea/18253](http://brainstorm.ubuntu.com/idea/18253)
[http://ubuntuforums.org/showthread.php?t=635015](http://ubuntuforums.org/showthread.php?t=635015)

[http://www.canonical.com/enterprise-services/landscape](http://www.canonical.com/enterprise-services/landscape)

[http://www.workswithu.com/2010/07/23/active-directory-integration-centrify-express-vs-likewise/](http://www.workswithu.com/2010/07/23/active-directory-integration-centrify-express-vs-likewise/)

[http://www.centrify.com/express/centrify-express-overview.asp](http://www.centrify.com/express/centrify-express-overview.asp)
[http://www.likewise.com/products/likewise_open/index.php](http://www.likewise.com/products/likewise_open/index.php)


[http://www.centrify.com/products/overview.asp](http://www.centrify.com/products/overview.asp)

[http://www.likewise.com/products/likewise_enterprise/index.php](http://www.likewise.com/products/likewise_enterprise/index.php)
[http://www.likewise.com/products/likewise_enterprise/group_policy.php](http://www.likewise.com/products/likewise_enterprise/group_policy.php)
[http://www.likewise.com/products/likewise_enterprise/ubuntu-group-policy.php](http://www.likewise.com/products/likewise_enterprise/ubuntu-group-policy.php)
[http://www.likewise.com/products/likewise_enterprise/gnome_group_policy.php](http://www.likewise.com/products/likewise_enterprise/gnome_group_policy.php)

[http://www.likewise.com/resources/documentation_library/manuals/lwe/group-policy-guide.html](http://www.likewise.com/resources/documentation_library/manuals/lwe/group-policy-guide.html)
[http://www.centrify.com/directcontrol/grouppolicy.asp](http://www.centrify.com/directcontrol/grouppolicy.asp)

[https://help.ubuntu.com/community/KickstartCompatibility](https://help.ubuntu.com/community/KickstartCompatibility)
[https://help.ubuntu.com/10.04/installation-guide/i386/automatic-install.html](https://help.ubuntu.com/10.04/installation-guide/i386/automatic-install.html)

[https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo)
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)


[http://landofthefreeish.com/linux/howto-add-a-linux-server-to-windows-server-2003-active-directory-domain/](http://landofthefreeish.com/linux/howto-add-a-linux-server-to-windows-server-2003-active-directory-domain/)
[http://www.ubuntugeek.com/how-to-add-ubuntu-804-to-win-server-2003-active-directory-domain.html](http://www.ubuntugeek.com/how-to-add-ubuntu-804-to-win-server-2003-active-directory-domain.html)

---

