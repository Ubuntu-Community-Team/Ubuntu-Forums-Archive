---
title: "ATI 3870 w/ duo Monitor settings will not save."
date: 2008-11-04
forum: Desktop Environments
---

### Post by brian77095 on 2008-11-04
Need help with my dual monitor setup.  Before the upgrade I had this working perfectly.  Now every time I log on it defaults to mirror image dual screen.  When I go to change the settings it says I must restart when I restart it comes back the same mirror image.

Do I need to reinstall the drivers?

I am running 8.1 and have ATI 3870.  I am making the changes in the Catalyst Control Center.

Thanks for the help.  I searched for a previous post bud did not find one.

---

### Post by brian77095 on 2008-11-07
Does anyone use Catalyst Control Center?

Can I try different drivers to with this Display manager?

---

### Post by svamppi on 2008-11-27
Same problem for me. Radeon X1950 Pro with two different sized monitors always loads with cloned desktop on one screen. And yeah it also says I have to reboot for the settings to take effect.

---

### Post by svamppi on 2008-12-07
Well, apparently it's a known issue. From the Known Issues section in the release notes for the newest downloadable ati driver:

X will start in clone mode when “Big Desktop” mode is enabled using Cata-
lyst Control Center.

So let's hope ati can sort out their crappy linux drivers eventually.

---

### Post by ismogismo on 2009-01-26
This post should solve the problem:

[http://www.davehay.f2s.com/2008/12/solved-ati-catalyst-control-centre-not.html](http://www.davehay.f2s.com/2008/12/solved-ati-catalyst-control-centre-not.html)

---

### Post by kwatts on 2009-02-02
Same problem, with ati 3400 using the ati proprietary driver and using amdcccle. The apply 'fix' doesn't work.

---

### Post by kdreimiller on 2009-02-05
that apply fix worked!  i totally didnt think it would, but it worked perfectly.  now boots with my big display to the right, as i wanted it.  thanks.

---

### Post by brolin on 2009-03-04
I am in the same situation as kdreimiller:  I did not expect the suggested fix to work, but it does! :D  This is with an Asus EAH3650 video card on Ubuntu 8.10 Desktop i386.

---

### Post by noogs on 2009-03-22
Apply fix works perfectly no issues anymore yay.

---

