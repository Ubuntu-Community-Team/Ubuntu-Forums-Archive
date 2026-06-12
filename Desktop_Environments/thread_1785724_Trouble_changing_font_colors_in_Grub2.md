---
title: "Trouble changing font colors in Grub2"
date: 2011-06-18
forum: Desktop Environments
---

### Post by fritzman on 2011-06-18
I've been trying to change the font colors in Grub2, but nothing seems to affect it.  The font always comes out light-gray.  Yet, this is my /etc/grub.d/05_debian_theme;
al@uglybox:~$ sudo gedit /etc/grub.d/05_debian_theme
#!/bin/sh
set -e

# grub-mkconfig helper script.
# Copyright (C) 2010  Alexander Kurtz <kurtz.alex@googlemail.com>
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

# Include the GRUB helper library for grub-mkconfig.
. /usr/lib/grub/grub-mkconfig_lib

# We want to work in /boot/grub/ only.
test -d "${GRUB_PREFIX}"; cd "${GRUB_PREFIX}"

# Set the location of a possibly necessary cache file for the background image.
# NOTE: This MUST BE A DOTFILE to avoid confusing it with user-defined images.
BACKGROUND_CACHE=".background_cache"

set_default_theme(){
	# Set a monochromatic theme for Ubuntu.
	echo "${1}set menu_color_normal=**light-cyan/black**"
	echo "${1}set menu_color_highlight=**white/black**"
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
(I did not include all of the file, just the part regarding fonts.)

I have followed several of the 'how-to's' posted, including those on this forum, and nothing will change my font colors.  I must be missing something, but I don't know what.
Any help with this would really be appreciated

---

