---
title: "Conky: too many interfaces used (limit is 64)"
date: 2016-08-16
forum: Desktop Environments
---

### Post by os2 on 2016-08-16
Has anyone seen this error? Results in segfault after conky (1.10.1) has been running for a while.

```

conky: too many interfaces used (limit is 64)

```


```

conky.config = {
   out_to_console = true,
   out_to_x = false,
   background = false,
   update_interval = 4,
   update_interval_on_battery = 10,
   total_run_times = 0,
   use_spacer = 'none',
   override_utf8_locale = true,
--    font = -*-terminus2-medium-r-*-*-12-*-*-*-*-*-*-*,
   times_in_seconds = true,
   short_units = true,
--    format_human_readable = false
};

-- \\u2000 full space
-- \\u2001
-- ...
-- \\u2009
-- \\u200a
-- \\u200b 0-space

conky.text = [[
\\x03\\ue419  ${cpu cpu0}% (${top name 1}) \\ue418 $memperc% (${top_mem name 1})  \\ue3ab $swap \\u2000 \\x04/ ${fs_used_perc /}% /var ${fs_used_perc  /var}% /home ${fs_used_perc /home}% /tmp ${fs_used_perc /tmp}% \\ue4a8  ${diskio_write nvme0n1} \\ue4a7 ${diskio_read nvme0n1} (${top_io name  1}) \\u2000 \\x05\\ue3dd ${wireless_essid wlp109s0}  (${wireless_link_qual_perc wlp109s0}%) ${execpi 60  /usr/local/sh/ip}${if_up ppp0} \\ue4a8 ${downspeedf ppp0}K (${totaldown  ppp0}) \\ue4a7 ${upspeedf ppp0}K (${totalup ppp0})$else \\ue4a8  ${downspeedf wlp109s0}K (${totaldown wlp109s0}) \\ue4a7 ${upspeedf  wlp109s0}K (${totalup wlp109s0})$endif \\u2000 \\x06\\ue35d  $battery_short ${format_time $battery_time "\hh \mm"} \\u2000  \\x07\\ue37f ${time %l:%M %a %d %b}
]];


```

---

