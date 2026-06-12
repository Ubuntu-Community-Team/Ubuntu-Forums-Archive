---
title: "Customizing login screen"
date: 2006-06-13
forum: Desktop Environments
---

### Post by arizonagroovejet on 2006-06-13
Can anyone enlighten me as to how to customize the KDM login screen?

If I go to System Settings > Login Manger it is quickly apparent that the settings shown there do not match what I see at the login screen. (E.g. there is a Greeting of 'Welcome to Kubuntu at %n shown in the settings but it's no where to be seen at the login screen.) Settings I set there do not show up at the login screen. I'm currently wondering what the point of the Login Manger of System Settings is if the settings there aren't actually used.

---

### Post by Jucato on 2006-06-13
The Login Manager in System Settings or KControl is responsible for Login options and processes, not for the Login appearance.

In order to change the KDM Login appearance, you need to install the kdmtheme package. This will install the KDM Theme Manager and will put an entry in System Settings/KControl beside it.

Then you could go to KDE-Look.org and download some KDM Themes. Some of the themes there use engines like Moodin. Moodin is already installed by default in Dapper (unlike in Breezy) so you don't have to worry about that. Just download the KDM Theme (in .tar.gz format) and place it somewhere in your folders. 

Open up System Settings and choose KDM Theme Manager. Enter Administrator Mode and click on Install Theme. Browse to where you downloaded the KDM Theme and select it. It will now be installed together with the default Dapper theme. Click on the new theme and click Apply to save the changes. 

Hope that helps.

---

### Post by arizonagroovejet on 2006-06-13
[QUOTE=Fenyx]The Login Manager in System Settings or KControl is responsible for Login options and processes, not for the Login appearance.[/QUOTE]

If the Login Manger section in System Settings is not reposinsible for the Login appearance then why does it contain a tab called Appearance? Or tabs called Font and Background? If the settings in these tabs have no effect then why are they there?

To partly answer my own question I have now discovered that if you install the kdmtheme package and untick the box for 'Enable KDM Themes', then the settings in the aforementioned tabs do affect the appearance of the login screen.
So the settings in those tabs are relevant but only if you install a package which is not installed by default. In a default installation you are presented with a bunch of options for changing the apperance of the login screen that have no effect when you change them. Which I think is very unhelpful.


[QUOTE=Fenyx]
In order to change the KDM Login appearance, you need to install the kdmtheme package. This will install the KDM Theme Manager and will put an entry in System Settings/KControl beside it.[/QUOTE]

Yep, worked just like you said, thanks.

However now after I installed a new theme and logged out and in again to test it, the original theme is no longer listed. Anyone know how I get that back?

---

### Post by Jucato on 2006-06-13
[QUOTE=arizonagroovejet]To partly answer my own question I have now discovered that if you install the kdmtheme package and untick the box for 'Enable KDM Themes', then the settings in the aforementioned tabs do affect the appearance of the login screen.[/QUOTE]

Never knew that. Thanks for the info. I guess it goes to show you learn something new in Linux everyday.

> In a default installation you are presented with a bunch of options for changing the apperance of the login screen that have no effect when you change them. Which I think is very unhelpful.

Different distros do things differently. Kubuntu has chosen to use a KDM theme engine called Moodin as the default. Probably other distros don't use KDM themes at all. But I don't know why they decided not to included the KDM Theme Manager. Probably they think that most users wouldn't bother with KDM Themes, and if they do, they'd know where to ask.

> However now after I installed a new theme and logged out and in again to test it, the original theme is no longer listed. Anyone know how I get that back?

In the /etc/kde3/kdm folder, open kdmrc (edit as root). There are two lines that would be of interest in this particular situation:
> Theme=/usr/share/apps/kdm/themes/*your_kdm_theme*
Themes=*list_of_installed_KDM_themes*
In the **Themes** line, insert this after the last KDM Theme:
> /usr/share/apps/kdm/themes/kubuntu
For example, this is what my Themes line looks like:
> Themes=/usr/share/apps/kdm/themes/Krystal,/usr/share/apps/kdm/themes/Linux Passion,/usr/share/apps/kdm/themes/kubuntu

Hope that helps.

---

