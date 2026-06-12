---
title: "Colour Management on Dual or Joined Display?"
date: 2019-08-13
forum: Desktop Environments
---

### Post by surferX on 2019-08-13
I have two screens,  the laptop screen which is a regular laptop screen, and a wide gamut monitor. I have created ICM profiles for both.

When I manually "hard code" those profiles in firefox (using about:config gfx.color_management.display_profile) and other programs it all works as expected. i.e. I get the colour I expect.

However just using ubuntu Device Colour Profiles GUI and setting the relevant profile for each, and then joining the displays is not working as expected.

It does the following:

1. For the joined display it just uses the first profile to render the background image of unity. (actually the hole gnome desktop simply ignores this second profile for the external monitor)
2. Firefox just uses the 1st profile regardless of position of the firefox window on the 2nd display.
3. Rawthereperee uses the 1st profile etc.

Is there a way to better support colour management on joined displays?

---

