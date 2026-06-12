---
title: "REQ: Please post unmodified &quot;fontconfig-config.config&quot; shell script"
date: 2007-06-19
forum: Desktop Effects &amp; Customization
---

### Post by dkim68 on 2007-06-19
Could someone please post the original unmodified "fontconfig-config.config" file located in /var/lib/dpkg/info

I messed up and didn't backup the original file.

Thanks!

---

### Post by coffeecat on 2007-06-19
```
#! /bin/sh

set -e

. /usr/share/debconf/confmodule

CONFDIR=/etc/fonts/conf.d

hinting_type="Native"

unhinted_2_3="10-debconf-unhinted.conf"
unhinted_2_4="10-unhinted.conf"
autohint_2_3="10-debconf-autohint.conf"
autohint_2_4="10-autohint.conf"

if [ -h $CONFDIR/$unhinted_2_4 -o -h $CONFDIR/$unhinted_2_3 ]; then
        hinting_type="None"
fi
if [ -h $CONFDIR/$autohint_2_4 -o -h $CONFDIR/$autohint_2_3 ]; then
        hinting_type="Autohinter"
fi

db_set fontconfig/hinting_type "$hinting_type"


subpixel_rendering="Automatic"

subpixel_2_3="20-debconf-sub-pixel.conf"
subpixel_2_4="10-sub-pixel.conf"
no_subpixel_2_3="20-debconf-no-sub-pixel.conf"
no_subpixel_2_4="10-no-sub-pixel.conf"

if [ -h $CONFDIR/$subpixel_2_4 -o -h $CONFDIR/$subpixel_2_3 ]; then
        subpixel_rendering="Always"
fi

if [ -h $CONFDIR/$no_subpixel_2_4 -o -h $CONFDIR/$no_subpixel_2_3 ]; then
        subpixel_rendering="Never"
fi

db_set fontconfig/subpixel_rendering "$subpixel_rendering"


# convert old debconf -> new debconf -> current debconf
if [ -f /var/lib/fontconfig/local.conf ]; then
  # old -> current
  if db_get fontconfig/subpixel_rendering; then
    if [ "$RET" = true ]; then
      db_set fontconfig/subpixel_rendering "Always"
      db_set fontconfig/hinting_type "Native"
    fi
  fi
  # new -> current
  if db_get fontconfig/rendering_type; then
    case "$RET" in
    "Subpixel rendering (LCD screens)")
      db_set fontconfig/subpixel_rendering "Always"
      db_set fontconfig/hinting_type "Native"
      ;;
    "Bytecode interpreter (CRT screens)")
      db_set fontconfig/subpixel_rendering "Never"
      db_set fontconfig/hinting_type "Native"
      ;;
    "Autohinter")
      db_set fontconfig/subpixel_rendering "Automatic"
      db_set fontconfig/hinting_type "Autohinter"
      ;;
    esac
    db_unregister fontconfig/rendering_type || true
  fi
fi

yes_bitmaps_2_3="30-debconf-yes-bitmaps.conf"
yes_bitmaps_2_4="70-yes-bitmaps.conf"
no_bitmaps_2_3="30-debconf-no-bitmaps.conf"
no_bitmaps_2_4="70-no-bitmaps.conf"

if [ -h $CONFDIR/$yes_bitmaps_2_4 -o -h $CONFDIR/$yes_bitmaps_2_3 ]; then
        db_set fontconfig/enable_bitmaps true
elif [ -h $CONFDIR/$no_bitmaps_2_4 -o -h $CONFDIR/$no_bitmaps_2_3 ]; then
        db_set fontconfig/enable_bitmaps false
fi

db_input low fontconfig/hinting_type || true
db_input low fontconfig/subpixel_rendering || true
db_input low fontconfig/enable_bitmaps || true
db_go

```I've run dpkg-reconfigure fontconfig-config to enable autohinting, but I assume that would not have modified that code.

---

