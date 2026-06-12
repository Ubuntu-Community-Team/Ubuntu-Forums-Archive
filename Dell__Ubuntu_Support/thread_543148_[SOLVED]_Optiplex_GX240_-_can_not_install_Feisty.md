---
title: "[SOLVED] Optiplex GX240 - can not install Feisty"
date: 2007-09-04
forum: Dell  Ubuntu Support
---

### Post by stanzap on 2007-09-04
I have an (old) Optiplex GX240 with (upgraded) 512MB and an (upgraded) 200GB drive in it.  I've tried numerous times to install Edgy and Feisty but had no luck.  Solution that worked for me was to update BIOS to A03 and add 'acpi=force' to kernel options.  Install proceeds normally with Feisty Alternate ISO.  Live CD's for Edgy and Feisty never worked.  Post I've found that mentioned this follows:

--- Andrew Morton <akpm@linux-foundation.org> wrote:
> On Sat, 12 May 2007 07:04:25 -0700 (PDT) Tear <tarrqt@yahoo.com> wrote:
> 
> > Summary: If ACPI is not enabled but APIC is,
> > then there is trouble on Dell Optiplex GX240.
> > If both are enabled or if both are disabled, then
> > everything is fine. The attached patch removes
> > Dell Optiplex GX240 from the ACPI blacklist.
> > 
> > ---
> > 
> > Hello,
> > 
> > I have a Dell Optiplex GX240 and when I boot Linux, ACPI
> > gets set up by only acpi=ht. dmesg shows the following line:
> > 
> >    DELL GX240 detected: force use of acpi=ht
> > 
> > Everything seemed to be fine. However, I discovered that
> > everything is not fine. The USB controller works so slowly
> > that copying a few (uncached) 1 megabyte large photos from
> > a USB-enabled digital camera takes many minutes instead of
> > a couple of seconds.
> > 
> > I am using Linux 2.6.21.1 on a Debian 4.0 ("Etch") system.
> > 
> > I thought that this might be related to ACPI. So I tried
> > to boot with _only_ "acpi=force" appended to the kernel
> > command line. Voila, the USB controller started to work
> > at full speed and copying photos from my digital camera
> > took only seconds.
> > 
> > I tested the system with "acpi=force" and could not find
> > anything which did not work. So, can we please remove
> > Dell Optiplex GX240 from the blacklist in
> > 
> > ..../arch/i386/kernel/acpi/boot.c
> > 
> > ? The attached patch does just that: It removes Dell
> > Optiplex GX240 from the ACPI blacklist.
> > 
> > I thought that this might be related to interrupts and
> > APIC as well. (Note that this is APIC, not ACPI.) I tried
> > booting with _only_ "noapic" and "nolapic" appended to the
> > command line. Again, the USB controller started to work
> > at full speed.
> > 
> > If removing Dell Optiplex GX240 from the ACPI blacklist
> > is not wanted/possible, then is there a way to disable
> > APIC and LAPIC (note that this is APIC not ACPI) by
> > default on Dell GX240 machines? (I.e. Can one patch
> > the kernel so that APIC and LAPIC isn't used on
> > these machines? - I know that I can use the noapic
> > and nolapic options on the kernel command line.)
> > 
> > Thank you for your attention.
> > 
> > - Tear
> > 
> > Note: Please include me in CC of your replies.
> > 
> > 
> > --- linux-2.6.21.1.orig/arch/i386/kernel/acpi/boot.c	2007-05-01 17:10:30.000000000 +0300
> > +++ linux-2.6.21.1/arch/i386/kernel/acpi/boot.c	2007-05-01 20:31:53.000000000 +0300
> > @@ -971,14 +971,6 @@
> >  	 },
> >  	{
> >  	 .callback = force_acpi_ht,
> > -	 .ident = "DELL GX240",
> > -	 .matches = {
> > -		     DMI_MATCH(DMI_BOARD_VENDOR, "Dell Computer Corporation"),
> > -		     DMI_MATCH(DMI_BOARD_NAME, "OptiPlex GX240"),
> > -		     },
> > -	 },
> > -	{
> > -	 .callback = force_acpi_ht,
> >  	 .ident = "HP VISUALIZE NT Workstation",
> >  	 .matches = {
> >  		     DMI_MATCH(DMI_BOARD_VENDOR, "Hewlett-Packard"),
> > 
> 
> Thanks.  Let's cc the acpi list.
> 
> The origin of that blacklist entry appears to be lost in the mists of time.
> git-blame got tripped up by an intervening Lindent run and my gittiness
> is insufficient for tracking changes before that.
> 

Mr. Morton,

I have already sent a very similar e-mail to the linux-acpi
mailing list. Please see the following for that:

[http://marc.info/?l=linux-acpi&m=117856470816834&w=2](http://marc.info/?l=linux-acpi&m=117856470816834&w=2)

I haven't received a reply and that is why sent this e-mail
to the linux-kernel mailing list.

I would be very pleased to see the removal of Dell Optiplex
GX240 from the ACPI blacklist.

Is there a blacklist for APIC? (Note that this is APIC,
not ACPI.)

Thank you.

Tear




 ********************************************
 Stan Zapaticky    | ZAP Consultants
 Tel (613)226-7376 | stan at ZAP Consultants dot com
 Fax (253)295-4420 | [www.zapconsultants.com](www.zapconsultants.com)

---

