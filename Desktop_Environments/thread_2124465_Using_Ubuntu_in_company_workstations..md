---
title: "Using Ubuntu in company workstations."
date: 2013-03-11
forum: Desktop Environments
---

### Post by Yourname on 2013-03-11
Hello!

Our company has about 150 workstations. So far on Windows, and the time has come for us to figure out licensing. It's turning out to be heavy.
The majority of the workstations use browser for our crm and email, a sip voip softphone, calculator, notepad and the ms office suite (which we're trying to push for google docs), pdf viewer, printer and also sysaid helpdesk software. So I'd say 100 stations have absolutely no need for windows style computing. We're into microloans so most of our work is contracts, paperwork, giving out loans, spreadsheets, etc.

I know that Ubuntu will work well as desktop for all these workstations and most of them will work out well. 
I just want to know if there's an Active Directory style workstation management system or something for this. 

Please let me know your thoughts.

---

### Post by jsabina1 on 2013-03-11
Great idea, I wish my company would do the same!
I was reading about samba4 or openldap as active directory alternative

---

### Post by grahammechanical on 2013-03-11
I do not know what Microsoft Active directory is. You can look at Landscape [http://www.ubuntu.com/business/systems-management/](http://www.ubuntu.com/business/systems-management/) There is a 30 day free trial. [http://www.canonical.com/enterprise-services/ubuntu-advantage](http://www.canonical.com/enterprise-services/ubuntu-advantage) I would not be surprised if your bosses who have been willing to pay Microsoft thousands, if not millions, over the years will now expect better quality for nothing. And expect you to get it working for no extra money in your pay packet.

---

### Post by Yourname on 2013-03-12
> **grahammechanical said:**
> I do not know what Microsoft Active directory is. You can look at Landscape [http://www.ubuntu.com/business/systems-management/](http://www.ubuntu.com/business/systems-management/) There is a 30 day free trial. [http://www.canonical.com/enterprise-services/ubuntu-advantage](http://www.canonical.com/enterprise-services/ubuntu-advantage) I would not be surprised if your bosses who have been willing to pay Microsoft thousands, if not millions, over the years will now expect better quality for nothing. And expect you to get it working for no extra money in your pay packet.

Yeah, but thankfully I am the guy in charge of technical and if I say it will save costs, it will work well.

---

### Post by SeijiSensei on 2013-03-13
What about retraining costs?  Do you have Excel spreadsheet applications with macros or scripting?  They may not migrate well.

Are you sure you want to move all your proprietary information into the cloud?  Why not use Open/LibreOffice on the desktops?

Have you looked into [Novell ZENworks]("http://www.novell.com/products/zenworks/linuxmanagement/") as a centralized management option?

---

### Post by Yourname on 2013-03-13
> **SeijiSensei said:**
> What about retraining costs?  Do you have Excel spreadsheet applications with macros or scripting?  They may not migrate well.

Are you sure you want to move all your proprietary information into the cloud?  Why not use Open/LibreOffice on the desktops?

Have you looked into [Novell ZENworks]("http://www.novell.com/products/zenworks/linuxmanagement/") as a centralized management option?

Retraining won't be an issue since 95% of their jobs are on the browser, thankfully. And logging in shouldn't be an issue. (I would prefer a central user database to log into, like Windows AD)
OpenOffice might work, but sometimes the formats don't jive well. Hence, Google Docs. We prefer to have all this data in the cloud because it's cost-effective, and pretty secure. Email is Google, and CRM is Zoho. Moving CRM to a local database has maintenance costs, and more headaches in terms of finding a systems admin, etc. 

I'm pretty much looking for a deployment solutions for Ubuntu to see if I can have users logged into an AD Style server, and all our other services also authenticate into AD (Helpdesk like SysAid, Google Apps/Email) and management and restrictions for these Ubuntu users. Finally, barebones PXE provisioning, if at all.

---

### Post by SeijiSensei on 2013-03-13
Linux uses something called "pluggable authentication modules" or "PAM" to handle user authentication.  There are PAM modules to handle just about any method you would like. You can tell the Ubuntu clients to authenticate against a server running NIS or OpenLDAP.  I've never found LDAP especially admin-friendly, but there are probably better tools available these days to build the required databases than when I last looked into LDAP.

Active Directory uses Microsoft's versions of the LDAP and Kerberos standards that were originally developed for Unix.  Again I suspect that Novell and RedHat probably have better-developed tools for these types of network services than Ubuntu.  Another option is [Samba 4]("https://wiki.samba.org/index.php/Samba4/Status"), but as it is quite new, I have never used it myself.

---

### Post by lingpanda on 2013-03-15
> **Yourname said:**
> Hello!

Our company has about 150 workstations. So far on Windows, and the time has come for us to figure out licensing. It's turning out to be heavy.
The majority of the workstations use browser for our crm and email, a sip voip softphone, calculator, notepad and the ms office suite (which we're trying to push for google docs), pdf viewer, printer and also sysaid helpdesk software. So I'd say 100 stations have absolutely no need for windows style computing. We're into microloans so most of our work is contracts, paperwork, giving out loans, spreadsheets, etc.

I know that Ubuntu will work well as desktop for all these workstations and most of them will work out well. 
I just want to know if there's an Active Directory style workstation management system or something for this. 

Please let me know your thoughts.

[https://wiki.samba.org/index.php/Samba_AD_DC_HOWTO](https://wiki.samba.org/index.php/Samba_AD_DC_HOWTO)

[http://www.beyondtrust.com/Products/PowerBrokerIdentityServicesADBridge/](http://www.beyondtrust.com/Products/PowerBrokerIdentityServicesADBridge/)

---

### Post by Yourname on 2013-03-17
> **lingpanda said:**
> [https://wiki.samba.org/index.php/Samba_AD_DC_HOWTO](https://wiki.samba.org/index.php/Samba_AD_DC_HOWTO)

[http://www.beyondtrust.com/Products/PowerBrokerIdentityServicesADBridge/](http://www.beyondtrust.com/Products/PowerBrokerIdentityServicesADBridge/)

Thanks guys!

---

