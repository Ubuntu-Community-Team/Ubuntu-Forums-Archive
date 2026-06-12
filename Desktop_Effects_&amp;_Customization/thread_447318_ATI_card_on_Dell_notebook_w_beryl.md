---
title: "ATI card on Dell notebook w/ beryl"
date: 2007-05-17
forum: Desktop Effects &amp; Customization
---

### Post by unconquerable on 2007-05-17
I am looking at buying the Dell 1501 below.  It has an ATI card, will this work OK with ubuntu and beryl?  I don't want to have a non functioning computer that is brand new!  I am alright with doing some tweaking, but I do not want it to be too hard.

Should I just wait for a better card?

I want to pull the trigger and buy!

[http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=04&kc=6W300&l=en&oc=bndwh2c&s=bsd](http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=04&kc=6W300&l=en&oc=bndwh2c&s=bsd)

---

### Post by unconquerable on 2007-05-17
Shoot, now they made it so you can only get it with DELL wireless, is this going to be a problem?

CRAP!!!

---

### Post by shen-an-doah on 2007-05-17
I use an Inspiron 1501 and Beryl works great on it.

This site is awesome for doing stuff with Ubuntu on a 1501:

[http://ubuntu1501.blogspot.com/](http://ubuntu1501.blogspot.com/)

---

### Post by unconquerable on 2007-05-17
> **shen-an-doah said:**
> I use an Inspiron 1501 and Beryl works great on it.

This site is awesome for doing stuff with Ubuntu on a 1501:

[http://ubuntu1501.blogspot.com/](http://ubuntu1501.blogspot.com/)



Is the dell wireless card working of for you.  What is a mini-card, it is not removable wireless is it?

THANKS!

---

### Post by shen-an-doah on 2007-05-17
My wireless has been iffy. It's worked before but then suddenly stopped working for no reason. It may just be mine though as Red (the guy who does the Ubuntu1501 blog) reckons his guide should work fine.

No idea what the mini-card thing means. Mine's not removable at least...

---

### Post by krisfrajer on 2007-05-17
I have an ATI card but I have not be able to set it up properly. My card is a radeon 9600XT series. What type of card do you have? Also my architecture is AMD64 which is a bit different than yours. Still installing a video card properly requires some experience. Good luck!

---

### Post by shen-an-doah on 2007-05-17
Mine is a ATI RADEON® Xpress1150 256MB HyperMemory, which is what comes in the 1501 as standard, it seems.

My processor's AMD64 too, but I got annoyed with stuff not being available for 64-bit systems, so I'm using the 32-bit version of feisty.

---

### Post by antw on 2007-05-18
I have the 1501 and beryl works fine. I have 7.04 ubuntu installed and it very fast. I am using the upgraded wifi open driver but am only able to get a connection of 11MBps out of it. I read also that with the new kennel out soon that it will fix this slow speed. Ndiswrapper failed to work for me, not sure why as I am using it successfully on another computer. 

I am dual booting with vista and am finding that I rarely boot into it.

---

### Post by peacekpr on 2007-05-26
> **unconquerable said:**
> I am looking at buying the Dell 1501 below.  It has an ATI card, will this work OK with ubuntu and beryl?  I don't want to have a non functioning computer that is brand new!  I am alright with doing some tweaking, but I do not want it to be too hard.

Should I just wait for a better card?

I want to pull the trigger and buy!

[http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=04&kc=6W300&l=en&oc=bndwh2c&s=bsd](http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=04&kc=6W300&l=en&oc=bndwh2c&s=bsd)

I use Ubuntu Edgy AMD64.  Beryl works.  Wireless works (with ndiswrapper).  I don't really have any problems...not to say that I didn't have to spend considerable time figuring things out.  So, it took some time getting it all up to snuff, but my computer is functioning just fine. :-)  There are some annoying video codec issues, but it's not anything that really bothers me to the point of pulling my hair out.  Mediaplayerconnectivity for Iceweasel32 mostly takes care of my internet multimedia issues.

Regards.

---

### Post by lsutiger on 2007-06-01
Can someone step me through on how to setup the ATI driver?
I have been following the [steps here]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide"). I get error with the module assistant with this code:
```
sudo module-assistant build fglrx

```
How do I access the log for the module assistant so I can post it here?

I have the Dell 1501 with the ATI RADEON® Xpress1150 256MB HyperMemory.
My Wireless is working great!
I bought this so I could have 3D.
Thanx in advance!

Here is the log:
dh_testroot
rm -f configure-stamp
rm -f fglrx.ko fglrx.mod.c *.o libfglrx_ip.a
rm -f .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
rm -rf patch
dh_clean
rm /usr/src/modules/fglrx/debian/control
rm /usr/src/modules/fglrx/debian/dirs
if [ -f /usr/src/modules/fglrx/debian/control.template ]; then \
		cat /usr/src/modules/fglrx/debian/control.template > /usr/src/modules/fglrx/debian/control; \
	fi
if [ -f /usr/src/modules/fglrx/debian/postinst ]; then \
		mv /usr/src/modules/fglrx/debian/postinst /usr/src/modules/fglrx/debian/fglrx-kernel-2.6.20-16-generic.postinst; \
	fi
dh_testdir
touch configure-stamp
dh_testdir
/usr/bin/make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/usr/src/modules/fglrx modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/src/modules/fglrx/firegl_public.o
/usr/src/modules/fglrx/firegl_public.c:208: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;mlock&#8217;
/usr/src/modules/fglrx/firegl_public.c:208: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;addr&#8217;
/usr/src/modules/fglrx/firegl_public.c:208: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;len&#8217;
/usr/src/modules/fglrx/firegl_public.c:210: warning: return type defaults to &#8216;int&#8217;
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;_syscall2&#8217;:
/usr/src/modules/fglrx/firegl_public.c:210: error: expected declaration specifiers before &#8216;_syscall2&#8217;
/usr/src/modules/fglrx/firegl_public.c:243: error: parameter &#8216;__ke_debuglevel&#8217; is initialized
/usr/src/modules/fglrx/firegl_public.c:244: error: parameter &#8216;__ke_moduleflags&#8217; is initialized
/usr/src/modules/fglrx/firegl_public.c:247: error: storage class specified for parameter &#8216;__mod_author247&#8217;
/usr/src/modules/fglrx/firegl_public.c:247: error: parameter &#8216;__mod_author247&#8217; is initialized
/usr/src/modules/fglrx/firegl_public.c:247: warning: &#8216;__used__&#8217; attribute ignored
/usr/src/modules/fglrx/firegl_public.c:247: error: section attribute not allowed for &#8216;__mod_author247&#8217;
/usr/src/modules/fglrx/firegl_public.c:248: error: storage class specified for parameter &#8216;__mod_description248&#8217;
/usr/src/modules/fglrx/firegl_public.c:248: error: parameter &#8216;__mod_description248&#8217; is initialized
/usr/src/modules/fglrx/firegl_public.c:248: warning: &#8216;__used__&#8217; attribute ignored
/usr/src/modules/fglrx/firegl_public.c:248: error: section attribute not allowed for &#8216;__mod_description248&#8217;
/usr/src/modules/fglrx/firegl_public.c:252: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/usr/src/modules/fglrx/firegl_public.c:252: error: expected declaration specifiers before &#8216;;&#8217; token
/usr/src/modules/fglrx/firegl_public.c:252: error: storage class specified for parameter &#8216;__param_perm_check_firegl&#8217;
/usr/src/modules/fglrx/firegl_public.c:252: error: parameter &#8216;__param_perm_check_firegl&#8217; is initialized
/usr/src/modules/fglrx/firegl_public.c:252: error: storage class specified for parameter &#8216;__param_str_firegl&#8217;
/usr/src/modules/fglrx/firegl_public.c:252: error: parameter &#8216;__param_str_firegl&#8217; is initialized
/usr/src/modules/fglrx/firegl_public.c:252: error: storage class specified for parameter &#8216;__param_firegl&#8217;
/usr/src/modules/fglrx/firegl_public.c:252: error: parameter &#8216;__param_firegl&#8217; is initialized
/usr/src/modules/fglrx/firegl_public.c:252: warning: &#8216;__used__&#8217; attribute ignored
/usr/src/modules/fglrx/firegl_public.c:252: error: section attribute not allowed for &#8216;__param_firegl&#8217;
/usr/src/modules/fglrx/firegl_public.c:252: error: alignment may not be specified for &#8216;__param_firegl&#8217;
/usr/src/modules/fglrx/firegl_public.c:252: error: &#8216;firegl&#8217; undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:252: error: (Each undeclared identifier is reported only once
/usr/src/modules/fglrx/firegl_public.c:252: error: for each function it appears in.)
/usr/src/modules/fglrx/firegl_public.c:252: error: storage class specified for parameter &#8216;__mod_firegltype252&#8217;
/usr/src/modules/fglrx/firegl_public.c:252: error: parameter &#8216;__mod_firegltype252&#8217; is initialized
/usr/src/modules/fglrx/firegl_public.c:252: warning: &#8216;__used__&#8217; attribute ignored
/usr/src/modules/fglrx/firegl_public.c:252: error: section attribute not allowed for &#8216;__mod_firegltype252&#8217;
/usr/src/modules/fglrx/firegl_public.c:255: error: storage class specified for parameter &#8216;__mod_license255&#8217;
/usr/src/modules/fglrx/firegl_public.c:255: error: parameter &#8216;__mod_license255&#8217; is initialized
/usr/src/modules/fglrx/firegl_public.c:255: warning: &#8216;__used__&#8217; attribute ignored
/usr/src/modules/fglrx/firegl_public.c:255: error: section attribute not allowed for &#8216;__mod_license255&#8217;
/usr/src/modules/fglrx/firegl_public.c:261: error: parameter &#8216;__ke_UTS_RELEASE&#8217; is initialized
/usr/src/modules/fglrx/firegl_public.c:262: error: parameter &#8216;__ke_PAGE_SHIFT&#8217; is initialized
/usr/src/modules/fglrx/firegl_public.c:263: error: parameter &#8216;__ke_PAGE_SIZE&#8217; is initialized
/usr/src/modules/fglrx/firegl_public.c:264: error: parameter &#8216;__ke_PAGE_MASK&#8217; is initialized
/usr/src/modules/fglrx/firegl_public.c:265: error: parameter &#8216;__ke_LINUX_VERSION_CODE&#8217; is initialized
/usr/src/modules/fglrx/firegl_public.c:272: error: parameter &#8216;__ke_MODVERSIONS_State&#8217; is initialized
/usr/src/modules/fglrx/firegl_public.c:280: error: parameter &#8216;__ke_SMP_State&#8217; is initialized
/usr/src/modules/fglrx/firegl_public.c:286: error: parameter &#8216;__ke_PAE_State&#8217; is initialized
/usr/src/modules/fglrx/firegl_public.c:297: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/usr/src/modules/fglrx/firegl_public.c:299: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/usr/src/modules/fglrx/firegl_public.c:301: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/usr/src/modules/fglrx/firegl_public.c:303: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/usr/src/modules/fglrx/firegl_public.c:310: error: storage class specified for parameter &#8216;firegl_fops&#8217;
/usr/src/modules/fglrx/firegl_public.c:310: error: parameter &#8216;firegl_fops&#8217; is initialized
/usr/src/modules/fglrx/firegl_public.c:315: error: &#8216;ip_firegl_open&#8217; undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:316: error: &#8216;ip_firegl_release&#8217; undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:317: error: &#8216;ip_firegl_ioctl&#8217; undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:318: error: &#8216;ip_firegl_mmap&#8217; undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:333: error: storage class specified for parameter &#8216;device_t&#8217;
/usr/src/modules/fglrx/firegl_public.c:335: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;firegl_public_device&#8217;
In file included from /usr/src/modules/fglrx/firegl_public.c:341:
/usr/src/modules/fglrx/drm.h:104: error: storage class specified for parameter &#8216;drm_handle_t&#8217;
/usr/src/modules/fglrx/drm.h:105: error: storage class specified for parameter &#8216;drm_context_t&#8217;
/usr/src/modules/fglrx/drm.h:106: error: storage class specified for parameter &#8216;drm_drawable_t&#8217;
/usr/src/modules/fglrx/drm.h:107: error: storage class specified for parameter &#8216;drm_magic_t&#8217;
/usr/src/modules/fglrx/drm.h:124: error: storage class specified for parameter &#8216;drm_clip_rect_t&#8217;
/usr/src/modules/fglrx/drm.h:136: error: storage class specified for parameter &#8216;drm_tex_region_t&#8217;
/usr/src/modules/fglrx/drm.h:148: error: storage class specified for parameter &#8216;drm_hw_lock_t&#8217;
/usr/src/modules/fglrx/drm.h:182: error: storage class specified for parameter &#8216;drm_version_t&#8217;
/usr/src/modules/fglrx/drm.h:193: error: storage class specified for parameter &#8216;drm_unique_t&#8217;
/usr/src/modules/fglrx/drm.h:199: error: expected specifier-qualifier-list before &#8216;drm_version_t&#8217;
/usr/src/modules/fglrx/drm.h:200: error: storage class specified for parameter &#8216;drm_list_t&#8217;
/usr/src/modules/fglrx/drm.h:205: error: storage class specified for parameter &#8216;drm_block_t&#8217;
/usr/src/modules/fglrx/drm.h:221: error: storage class specified for parameter &#8216;drm_control_t&#8217;
/usr/src/modules/fglrx/drm.h:233: error: storage class specified for parameter &#8216;drm_map_type_t&#8217;
/usr/src/modules/fglrx/drm.h:247: error: storage class specified for parameter &#8216;drm_map_flags_t&#8217;
/usr/src/modules/fglrx/drm.h:253: error: storage class specified for parameter &#8216;drm_ctx_priv_map_t&#8217;
/usr/src/modules/fglrx/drm.h:265: error: expected specifier-qualifier-list before &#8216;drm_map_type_t&#8217;
/usr/src/modules/fglrx/drm.h:271: error: storage class specified for parameter &#8216;drm_map_t&#8217;
/usr/src/modules/fglrx/drm.h:284: error: storage class specified for parameter &#8216;drm_client_t&#8217;
/usr/src/modules/fglrx/drm.h:306: error: storage class specified for parameter &#8216;drm_stat_type_t&#8217;
/usr/src/modules/fglrx/drm.h:316: error: expected specifier-qualifier-list before &#8216;drm_stat_type_t&#8217;
/usr/src/modules/fglrx/drm.h:318: error: storage class specified for parameter &#8216;drm_stats_t&#8217;
/usr/src/modules/fglrx/drm.h:334: error: storage class specified for parameter &#8216;drm_lock_flags_t&#8217;
/usr/src/modules/fglrx/drm.h:344: error: expected specifier-qualifier-list before &#8216;drm_lock_flags_t&#8217;
/usr/src/modules/fglrx/drm.h:345: error: storage class specified for parameter &#8216;drm_lock_t&#8217;
/usr/src/modules/fglrx/drm.h:375: error: storage class specified for parameter &#8216;drm_dma_flags_t&#8217;
/usr/src/modules/fglrx/drm.h:397: error: storage class specified for parameter &#8216;drm_buf_desc_t&#8217;
/usr/src/modules/fglrx/drm.h:405: error: expected specifier-qualifier-list before &#8216;drm_buf_desc_t&#8217;
/usr/src/modules/fglrx/drm.h:406: error: storage class specified for parameter &#8216;drm_buf_info_t&#8217;
/usr/src/modules/fglrx/drm.h:415: error: storage class specified for parameter &#8216;drm_buf_free_t&#8217;
/usr/src/modules/fglrx/drm.h:428: error: storage class specified for parameter &#8216;drm_buf_pub_t&#8217;
/usr/src/modules/fglrx/drm.h:437: error: expected specifier-qualifier-list before &#8216;drm_buf_pub_t&#8217;
/usr/src/modules/fglrx/drm.h:438: error: storage class specified for parameter &#8216;drm_buf_map_t&#8217;
/usr/src/modules/fglrx/drm.h:453: error: expected specifier-qualifier-list before &#8216;drm_dma_flags_t&#8217;
/usr/src/modules/fglrx/drm.h:459: error: storage class specified for parameter &#8216;drm_dma_t&#8217;
/usr/src/modules/fglrx/drm.h:465: error: storage class specified for parameter &#8216;drm_ctx_flags_t&#8217;
/usr/src/modules/fglrx/drm.h:474: error: expected specifier-qualifier-list before &#8216;drm_context_t&#8217;
/usr/src/modules/fglrx/drm.h:476: error: storage class specified for parameter &#8216;drm_ctx_t&#8217;
/usr/src/modules/fglrx/drm.h:484: error: expected specifier-qualifier-list before &#8216;drm_ctx_t&#8217;
/usr/src/modules/fglrx/drm.h:485: error: storage class specified for parameter &#8216;drm_ctx_res_t&#8217;
/usr/src/modules/fglrx/drm.h:492: error: expected specifier-qualifier-list before &#8216;drm_drawable_t&#8217;
/usr/src/modules/fglrx/drm.h:493: error: storage class specified for parameter &#8216;drm_draw_t&#8217;
/usr/src/modules/fglrx/drm.h:500: error: expected specifier-qualifier-list before &#8216;drm_magic_t&#8217;
/usr/src/modules/fglrx/drm.h:501: error: storage class specified for parameter &#8216;drm_auth_t&#8217;
/usr/src/modules/fglrx/drm.h:514: error: storage class specified for parameter &#8216;drm_irq_busid_t&#8217;
/usr/src/modules/fglrx/drm.h:521: error: storage class specified for parameter &#8216;drm_vblank_seq_type_t&#8217;
/usr/src/modules/fglrx/drm.h:528: error: expected specifier-qualifier-list before &#8216;drm_vblank_seq_type_t&#8217;
/usr/src/modules/fglrx/drm.h:531: warning: empty declaration
/usr/src/modules/fglrx/drm.h:535: error: expected specifier-qualifier-list before &#8216;drm_vblank_seq_type_t&#8217;
/usr/src/modules/fglrx/drm.h:539: warning: empty declaration
/usr/src/modules/fglrx/drm.h:550: error: storage class specified for parameter &#8216;drm_wait_vblank_t&#8217;
/usr/src/modules/fglrx/drm.h:560: error: storage class specified for parameter &#8216;drm_agp_mode_t&#8217;
/usr/src/modules/fglrx/drm.h:573: error: storage class specified for parameter &#8216;drm_agp_buffer_t&#8217;
/usr/src/modules/fglrx/drm.h:584: error: storage class specified for parameter &#8216;drm_agp_binding_t&#8217;
/usr/src/modules/fglrx/drm.h:606: error: storage class specified for parameter &#8216;drm_agp_info_t&#8217;
/usr/src/modules/fglrx/drm.h:615: error: storage class specified for parameter &#8216;drm_scatter_gather_t&#8217;
/usr/src/modules/fglrx/drm.h:625: error: storage class specified for parameter &#8216;drm_set_version_t&#8217;
/usr/src/modules/fglrx/firegl_public.c:347: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
In file included from include/linux/poll.h:4,
                 from /usr/src/modules/fglrx/drmP.h:82,
                 from /usr/src/modules/fglrx/drm_proc.h:41,
                 from /usr/src/modules/fglrx/firegl_public.c:357:
include/asm/poll.h:25: warning: empty declaration
In file included from /usr/src/modules/fglrx/drmP.h:82,
                 from /usr/src/modules/fglrx/drm_proc.h:41,
                 from /usr/src/modules/fglrx/firegl_public.c:357:
include/linux/poll.h:24: warning: empty declaration
include/linux/poll.h:29: error: storage class specified for parameter &#8216;poll_queue_proc&#8217;
include/linux/poll.h:32: error: expected specifier-qualifier-list before &#8216;poll_queue_proc&#8217;
include/linux/poll.h:33: error: storage class specified for parameter &#8216;poll_table&#8217;
include/linux/poll.h:35: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;poll_table&#8217;
include/linux/poll.h:36: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
include/linux/poll.h:41: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
include/linux/poll.h:50: warning: empty declaration
include/linux/poll.h:56: error: expected specifier-qualifier-list before &#8216;poll_table&#8217;
include/linux/poll.h:61: warning: empty declaration
include/linux/poll.h:63: error: storage class specified for parameter &#8216;poll_initwait&#8217;
include/linux/poll.h:64: error: storage class specified for parameter &#8216;poll_freewait&#8217;
include/linux/poll.h:73: error: storage class specified for parameter &#8216;fd_set_bits&#8217;
include/linux/poll.h:90: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
include/linux/poll.h:101: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
include/linux/poll.h:109: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
include/linux/poll.h:115: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;fd_set_bits&#8217;
include/linux/poll.h:115: error: storage class specified for parameter &#8216;do_select&#8217;
include/linux/poll.h:117: error: storage class specified for parameter &#8216;do_sys_poll&#8217;
In file included from /usr/src/modules/fglrx/drmP.h:83,
                 from /usr/src/modules/fglrx/drm_proc.h:41,
                 from /usr/src/modules/fglrx/firegl_public.c:357:
include/asm/pgalloc.h:36: error: storage class specified for parameter &#8216;pgd_alloc&#8217;
include/asm/pgalloc.h:37: error: storage class specified for parameter &#8216;pgd_free&#8217;
include/asm/pgalloc.h:39: error: storage class specified for parameter &#8216;pte_alloc_one_kernel&#8217;
include/asm/pgalloc.h:40: error: storage class specified for parameter &#8216;pte_alloc_one&#8217;
include/asm/pgalloc.h:43: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
include/asm/pgalloc.h:48: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
In file included from /usr/src/modules/fglrx/drm_proc.h:41,
                 from /usr/src/modules/fglrx/firegl_public.c:357:
/usr/src/modules/fglrx/drmP.h:126:1: warning: "DRM_DEBUG_CODE" redefined
/usr/src/modules/fglrx/firegl_public.c:177:1: warning: this is the location of the previous definition
In file included from /usr/src/modules/fglrx/drm_proc.h:41,
                 from /usr/src/modules/fglrx/firegl_public.c:357:
/usr/src/modules/fglrx/drmP.h:324: error: storage class specified for parameter &#8216;drm_ioctl_t&#8217;
/usr/src/modules/fglrx/drmP.h:327: error: expected specifier-qualifier-list before &#8216;drm_ioctl_t&#8217;
/usr/src/modules/fglrx/drmP.h:330: error: storage class specified for parameter &#8216;drm_ioctl_desc_t&#8217;
/usr/src/modules/fglrx/drmP.h:334: error: storage class specified for parameter &#8216;drm_devstate_t&#8217;
/usr/src/modules/fglrx/drmP.h:337: error: expected specifier-qualifier-list before &#8216;drm_magic_t&#8217;
/usr/src/modules/fglrx/drmP.h:340: error: storage class specified for parameter &#8216;drm_magic_entry_t&#8217;
/usr/src/modules/fglrx/drmP.h:345: error: storage class specified for parameter &#8216;drm_magic_head_t&#8217;
/usr/src/modules/fglrx/drmP.h:351: error: storage class specified for parameter &#8216;drm_vma_entry_t&#8217;
/usr/src/modules/fglrx/drmP.h:382: error: storage class specified for parameter &#8216;drm_buf_t&#8217;
/usr/src/modules/fglrx/drmP.h:388: error: expected specifier-qualifier-list before &#8216;drm_buf_t&#8217;
/usr/src/modules/fglrx/drmP.h:394: error: storage class specified for parameter &#8216;drm_waitlist_t&#8217;
/usr/src/modules/fglrx/drmP.h:399: error: expected specifier-qualifier-list before &#8216;drm_buf_t&#8217;
/usr/src/modules/fglrx/drmP.h:406: error: storage class specified for parameter &#8216;drm_freelist_t&#8217;
/usr/src/modules/fglrx/drmP.h:414: error: expected specifier-qualifier-list before &#8216;drm_buf_t&#8217;
/usr/src/modules/fglrx/drmP.h:420: error: storage class specified for parameter &#8216;drm_buf_entry_t&#8217;
/usr/src/modules/fglrx/drmP.h:428: error: expected specifier-qualifier-list before &#8216;drm_magic_t&#8217;
/usr/src/modules/fglrx/drmP.h:438: error: storage class specified for parameter &#8216;drm_file_t&#8217;
/usr/src/modules/fglrx/drmP.h:454: error: expected specifier-qualifier-list before &#8216;drm_ctx_flags_t&#8217;
/usr/src/modules/fglrx/drmP.h:457: error: storage class specified for parameter &#8216;drm_queue_t&#8217;
/usr/src/modules/fglrx/drmP.h:463: error: expected specifier-qualifier-list before &#8216;drm_hw_lock_t&#8217;
/usr/src/modules/fglrx/drmP.h:467: error: storage class specified for parameter &#8216;drm_lock_data_t&#8217;
/usr/src/modules/fglrx/drmP.h:474: error: expected specifier-qualifier-list before &#8216;drm_buf_entry_t&#8217;
/usr/src/modules/fglrx/drmP.h:493: error: storage class specified for parameter &#8216;drm_device_dma_t&#8217;
/usr/src/modules/fglrx/drmP.h:535: error: storage class specified for parameter &#8216;drm_sg_mem_t&#8217;
/usr/src/modules/fglrx/drmP.h:539: error: expected specifier-qualifier-list before &#8216;drm_hw_lock_t&#8217;
/usr/src/modules/fglrx/drmP.h:540: error: storage class specified for parameter &#8216;drm_sigdata_t&#8217;
/usr/src/modules/fglrx/drmP.h:547: error: expected specifier-qualifier-list before &#8216;drm_map_t&#8217;
/usr/src/modules/fglrx/drmP.h:548: error: storage class specified for parameter &#8216;drm_map_list_t&#8217;
/usr/src/modules/fglrx/drmP.h:550: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;drm_local_map_t&#8217;
/usr/src/modules/fglrx/drmP.h:557: error: expected specifier-qualifier-list before &#8216;drm_context_t&#8217;
/usr/src/modules/fglrx/drmP.h:559: error: storage class specified for parameter &#8216;drm_ctx_list_t&#8217;
/usr/src/modules/fglrx/drmP.h:594: error: expected specifier-qualifier-list before &#8216;drm_stat_type_t&#8217;
/usr/src/modules/fglrx/drmP.h:684: error: storage class specified for parameter &#8216;drm_device_t&#8217;
/usr/src/modules/fglrx/drmP.h:692: error: storage class specified for parameter &#8216;FGLDRM_flags&#8217;
/usr/src/modules/fglrx/drmP.h:693: error: storage class specified for parameter &#8216;FGLDRM_parse_options&#8217;
/usr/src/modules/fglrx/drmP.h:694: error: storage class specified for parameter &#8216;FGLDRM_cpu_valid&#8217;
/usr/src/modules/fglrx/drmP.h:698: error: storage class specified for parameter &#8216;FGLDRM_version&#8217;
/usr/src/modules/fglrx/drmP.h:699: error: storage class specified for parameter &#8216;FGLDRM_open&#8217;
/usr/src/modules/fglrx/drmP.h:700: error: storage class specified for parameter &#8216;FGLDRM_release&#8217;
/usr/src/modules/fglrx/drmP.h:702: error: storage class specified for parameter &#8216;FGLDRM_ioctl&#8217;
/usr/src/modules/fglrx/drmP.h:704: error: storage class specified for parameter &#8216;FGLDRM_lock&#8217;
/usr/src/modules/fglrx/drmP.h:706: error: storage class specified for parameter &#8216;FGLDRM_unlock&#8217;
/usr/src/modules/fglrx/drmP.h:707: error: storage class specified for parameter &#8216;FGLDRM_fb_loaded&#8217;
/usr/src/modules/fglrx/drmP.h:711: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;drm_device_t&#8217;
/usr/src/modules/fglrx/drmP.h:711: error: storage class specified for parameter &#8216;FGLDRM_open_helper&#8217;
/usr/src/modules/fglrx/drmP.h:712: error: storage class specified for parameter &#8216;FGLDRM_flush&#8217;
/usr/src/modules/fglrx/drmP.h:713: error: storage class specified for parameter &#8216;FGLDRM_fasync&#8217;
/usr/src/modules/fglrx/drmP.h:716: error: storage class specified for parameter &#8216;FGLDRM_vm_open&#8217;
/usr/src/modules/fglrx/drmP.h:717: error: storage class specified for parameter &#8216;FGLDRM_vm_close&#8217;
/usr/src/modules/fglrx/drmP.h:718: error: storage class specified for parameter &#8216;FGLDRM_vm_shm_close&#8217;
/usr/src/modules/fglrx/drmP.h:720: error: storage class specified for parameter &#8216;FGLDRM_mmap_dma&#8217;
/usr/src/modules/fglrx/drmP.h:721: error: storage class specified for parameter &#8216;FGLDRM_mmap&#8217;
/usr/src/modules/fglrx/drmP.h:722: error: storage class specified for parameter &#8216;FGLDRM_poll&#8217;
/usr/src/modules/fglrx/drmP.h:723: error: storage class specified for parameter &#8216;FGLDRM_read&#8217;
/usr/src/modules/fglrx/drmP.h:726: error: storage class specified for parameter &#8216;FGLDRM_mem_init&#8217;
/usr/src/modules/fglrx/drmP.h:728: error: storage class specified for parameter &#8216;FGLDRM_mem_info&#8217;
/usr/src/modules/fglrx/drmP.h:729: error: storage class specified for parameter &#8216;FGLDRM_alloc&#8217;
/usr/src/modules/fglrx/drmP.h:730: error: storage class specified for parameter &#8216;FGLDRM_calloc&#8217;
/usr/src/modules/fglrx/drmP.h:732: error: storage class specified for parameter &#8216;FGLDRM_realloc&#8217;
/usr/src/modules/fglrx/drmP.h:733: error: storage class specified for parameter &#8216;FGLDRM_free&#8217;
/usr/src/modules/fglrx/drmP.h:734: error: storage class specified for parameter &#8216;FGLDRM_alloc_pages&#8217;
/usr/src/modules/fglrx/drmP.h:736: error: storage class specified for parameter &#8216;FGLDRM_free_pages&#8217;
/usr/src/modules/fglrx/drmP.h:737: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;drm_device_t&#8217;
/usr/src/modules/fglrx/drmP.h:737: error: storage class specified for parameter &#8216;FGLDRM_ioremap&#8217;
/usr/src/modules/fglrx/drmP.h:739: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;drm_device_t&#8217;
/usr/src/modules/fglrx/drmP.h:739: error: storage class specified for parameter &#8216;FGLDRM_ioremap_nocache&#8217;
/usr/src/modules/fglrx/drmP.h:740: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;drm_device_t&#8217;
/usr/src/modules/fglrx/drmP.h:740: error: storage class specified for parameter &#8216;FGLDRM_ioremapfree&#8217;
/usr/src/modules/fglrx/drmP.h:751: error: storage class specified for parameter &#8216;FGLDRM_irq_by_busid&#8217;
/usr/src/modules/fglrx/drmP.h:753: error: storage class specified for parameter &#8216;FGLDRM_getunique&#8217;
/usr/src/modules/fglrx/drmP.h:755: error: storage class specified for parameter &#8216;FGLDRM_setunique&#8217;
/usr/src/modules/fglrx/drmP.h:757: error: storage class specified for parameter &#8216;FGLDRM_getmap&#8217;
/usr/src/modules/fglrx/drmP.h:759: error: storage class specified for parameter &#8216;FGLDRM_getclient&#8217;
/usr/src/modules/fglrx/drmP.h:761: error: storage class specified for parameter &#8216;FGLDRM_getstats&#8217;
/usr/src/modules/fglrx/drmP.h:763: error: storage class specified for parameter &#8216;FGLDRM_setversion&#8217;
/usr/src/modules/fglrx/drmP.h:767: error: storage class specified for parameter &#8216;FGLDRM_resctx&#8217;
/usr/src/modules/fglrx/drmP.h:769: error: storage class specified for parameter &#8216;FGLDRM_addctx&#8217;
/usr/src/modules/fglrx/drmP.h:771: error: storage class specified for parameter &#8216;FGLDRM_modctx&#8217;
/usr/src/modules/fglrx/drmP.h:773: error: storage class specified for parameter &#8216;FGLDRM_getctx&#8217;
/usr/src/modules/fglrx/drmP.h:775: error: storage class specified for parameter &#8216;FGLDRM_switchctx&#8217;
/usr/src/modules/fglrx/drmP.h:777: error: storage class specified for parameter &#8216;FGLDRM_newctx&#8217;
/usr/src/modules/fglrx/drmP.h:779: error: storage class specified for parameter &#8216;FGLDRM_rmctx&#8217;
/usr/src/modules/fglrx/drmP.h:781: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/src/modules/fglrx/drmP.h:782: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/src/modules/fglrx/drmP.h:790: error: storage class specified for parameter &#8216;FGLDRM_setsareactx&#8217;
/usr/src/modules/fglrx/drmP.h:792: error: storage class specified for parameter &#8216;FGLDRM_getsareactx&#8217;
/usr/src/modules/fglrx/drmP.h:796: error: storage class specified for parameter &#8216;FGLDRM_adddraw&#8217;
/usr/src/modules/fglrx/drmP.h:798: error: storage class specified for parameter &#8216;FGLDRM_rmdraw&#8217;
/usr/src/modules/fglrx/drmP.h:802: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/src/modules/fglrx/drmP.h:804: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/src/modules/fglrx/drmP.h:806: error: storage class specified for parameter &#8216;FGLDRM_getmagic&#8217;
/usr/src/modules/fglrx/drmP.h:808: error: storage class specified for parameter &#8216;FGLDRM_authmagic&#8217;
/usr/src/modules/fglrx/drmP.h:812: error: storage class specified for parameter &#8216;FGLDRM_noop&#8217;
/usr/src/modules/fglrx/drmP.h:816: error: storage class specified for parameter &#8216;FGLDRM_lock_take&#8217;
/usr/src/modules/fglrx/drmP.h:817: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/src/modules/fglrx/drmP.h:820: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/src/modules/fglrx/drmP.h:823: error: storage class specified for parameter &#8216;FGLDRM_notifier&#8217;
/usr/src/modules/fglrx/drmP.h:826: error: storage class specified for parameter &#8216;FGLDRM_order&#8217;
/usr/src/modules/fglrx/drmP.h:828: error: storage class specified for parameter &#8216;FGLDRM_addmap&#8217;
/usr/src/modules/fglrx/drmP.h:830: error: storage class specified for parameter &#8216;FGLDRM_rmmap&#8217;
/usr/src/modules/fglrx/drmP.h:898: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;drm_device_t&#8217;
/usr/src/modules/fglrx/drmP.h:902: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/src/modules/fglrx/drmP.h:908: error: storage class specified for parameter &#8216;FGLDRM_proc_cleanup&#8217;
/usr/src/modules/fglrx/drmP.h:911: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/src/modules/fglrx/drmP.h:914: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/src/modules/fglrx/drmP.h:918: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/src/modules/fglrx/drmP.h:921: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
In file included from /usr/src/modules/fglrx/firegl_public.c:357:
/usr/src/modules/fglrx/drm_proc.h:44: error: storage class specified for parameter &#8216;FGLDRM_name_info&#8217;
/usr/src/modules/fglrx/drm_proc.h:46: error: storage class specified for parameter &#8216;FGLDRM_vm_info&#8217;
/usr/src/modules/fglrx/drm_proc.h:48: error: storage class specified for parameter &#8216;FGLDRM_clients_info&#8217;
/usr/src/modules/fglrx/drm_proc.h:50: error: storage class specified for parameter &#8216;FGLDRM_queues_info&#8217;
/usr/src/modules/fglrx/drm_proc.h:52: error: storage class specified for parameter &#8216;FGLDRM_bufs_info&#8217;
/usr/src/modules/fglrx/drm_proc.h:55: error: storage class specified for parameter &#8216;FGLDRM_vma_info&#8217;
/usr/src/modules/fglrx/drm_proc.h:64: error: parameter &#8216;FGLDRM_proc_list&#8217; is initialized
/usr/src/modules/fglrx/drm_proc.h:65: warning: braces around scalar initializer
/usr/src/modules/fglrx/drm_proc.h:65: warning: (near initialization for &#8216;FGLDRM_proc_list&#8217;)
/usr/src/modules/fglrx/drm_proc.h:65: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/drm_proc.h:65: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/drm_proc.h:65: warning: (near initialization for &#8216;FGLDRM_proc_list&#8217;)
/usr/src/modules/fglrx/drm_proc.h:66: warning: braces around scalar initializer
/usr/src/modules/fglrx/drm_proc.h:66: warning: (near initialization for &#8216;FGLDRM_proc_list&#8217;)
/usr/src/modules/fglrx/drm_proc.h:66: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/drm_proc.h:66: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/drm_proc.h:66: warning: (near initialization for &#8216;FGLDRM_proc_list&#8217;)
/usr/src/modules/fglrx/drm_proc.h:66: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/drm_proc.h:66: warning: (near initialization for &#8216;FGLDRM_proc_list&#8217;)
/usr/src/modules/fglrx/drm_proc.h:67: warning: braces around scalar initializer
/usr/src/modules/fglrx/drm_proc.h:67: warning: (near initialization for &#8216;FGLDRM_proc_list&#8217;)
/usr/src/modules/fglrx/drm_proc.h:67: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/drm_proc.h:67: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/drm_proc.h:67: warning: (near initialization for &#8216;FGLDRM_proc_list&#8217;)
/usr/src/modules/fglrx/drm_proc.h:67: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/drm_proc.h:67: warning: (near initialization for &#8216;FGLDRM_proc_list&#8217;)
/usr/src/modules/fglrx/drm_proc.h:68: warning: braces around scalar initializer
/usr/src/modules/fglrx/drm_proc.h:68: warning: (near initialization for &#8216;FGLDRM_proc_list&#8217;)
/usr/src/modules/fglrx/drm_proc.h:68: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/drm_proc.h:68: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/drm_proc.h:68: warning: (near initialization for &#8216;FGLDRM_proc_list&#8217;)
/usr/src/modules/fglrx/drm_proc.h:68: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/drm_proc.h:68: warning: (near initialization for &#8216;FGLDRM_proc_list&#8217;)
/usr/src/modules/fglrx/drm_proc.h:69: warning: braces around scalar initializer
/usr/src/modules/fglrx/drm_proc.h:69: warning: (near initialization for &#8216;FGLDRM_proc_list&#8217;)
/usr/src/modules/fglrx/drm_proc.h:69: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/drm_proc.h:69: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/drm_proc.h:69: warning: (near initialization for &#8216;FGLDRM_proc_list&#8217;)
/usr/src/modules/fglrx/drm_proc.h:69: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/drm_proc.h:69: warning: (near initialization for &#8216;FGLDRM_proc_list&#8217;)
/usr/src/modules/fglrx/drm_proc.h:70: warning: braces around scalar initializer
/usr/src/modules/fglrx/drm_proc.h:70: warning: (near initialization for &#8216;FGLDRM_proc_list&#8217;)
/usr/src/modules/fglrx/drm_proc.h:70: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/drm_proc.h:70: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/drm_proc.h:70: warning: (near initialization for &#8216;FGLDRM_proc_list&#8217;)
/usr/src/modules/fglrx/drm_proc.h:70: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/drm_proc.h:70: warning: (near initialization for &#8216;FGLDRM_proc_list&#8217;)
/usr/src/modules/fglrx/drm_proc.h:72: warning: braces around scalar initializer
/usr/src/modules/fglrx/drm_proc.h:72: warning: (near initialization for &#8216;FGLDRM_proc_list&#8217;)
/usr/src/modules/fglrx/drm_proc.h:72: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/drm_proc.h:72: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/drm_proc.h:72: warning: (near initialization for &#8216;FGLDRM_proc_list&#8217;)
/usr/src/modules/fglrx/drm_proc.h:72: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/drm_proc.h:72: warning: (near initialization for &#8216;FGLDRM_proc_list&#8217;)
/usr/src/modules/fglrx/drm_proc.h:90: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/src/modules/fglrx/drm_proc.h:144: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/usr/src/modules/fglrx/drm_proc.h:174: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/usr/src/modules/fglrx/drm_proc.h:213: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token

---

### Post by lsutiger on 2007-06-01
The rest of the log:
/usr/src/modules/fglrx/drm_proc.h:269: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/drm_proc.h:292: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/drm_proc.h:339: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/drm_proc.h:362: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/drm_proc.h:409: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/drm_proc.h:432: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/drm_proc.h:466: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/drm_proc.h:480: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/drm_proc.h:537: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:363: error: storage class specified for parameter ‘drm_proclist’
/usr/src/modules/fglrx/firegl_public.c:363: error: parameter ‘drm_proclist’ is initialized
/usr/src/modules/fglrx/firegl_public.c:375: error: storage class specified for parameter ‘firegl_stub_list_t’
/usr/src/modules/fglrx/firegl_public.c:376: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘firegl_stub_list’
/usr/src/modules/fglrx/firegl_public.c:378: error: storage class specified for parameter ‘firegl_stub_root’
/usr/src/modules/fglrx/firegl_public.c:379: error: storage class specified for parameter ‘firegl_minor’
/usr/src/modules/fglrx/firegl_public.c:382: error: expected declaration specifiers or ‘...’ before ‘device_t’
/usr/src/modules/fglrx/firegl_public.c:385: error: storage class specified for parameter ‘firegl_drm_stub_info_t’
/usr/src/modules/fglrx/firegl_public.c:386: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘firegl_stub_info’
/usr/src/modules/fglrx/firegl_public.c:388: error: storage class specified for parameter ‘__ke_pte_phys_addr_str’
/usr/src/modules/fglrx/firegl_public.c:391: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:396: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:407: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:408: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:409: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:410: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:411: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:412: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:413: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:418: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:424: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:432: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:442: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:447: error: expected declaration specifiers or ‘...’ before ‘poll_table’
/usr/src/modules/fglrx/firegl_public.c:448: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:465: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:469: error: storage class specified for parameter ‘firegl_interrupt_file_ops’
/usr/src/modules/fglrx/firegl_public.c:469: error: parameter ‘firegl_interrupt_file_ops’ is initialized
/usr/src/modules/fglrx/firegl_public.c:470: error: ‘firegl_interrupt_open_wrap’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:471: error: ‘firegl_interrupt_read_wrap’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:472: error: ‘firegl_interrupt_release_wrap’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:473: error: ‘firegl_interrupt_poll_wrap’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:474: error: ‘firegl_interrupt_write_wrap’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:477: error: parameter ‘firegl_proc_list’ is initialized
/usr/src/modules/fglrx/firegl_public.c:479: warning: braces around scalar initializer
/usr/src/modules/fglrx/firegl_public.c:479: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:479: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c:479: error: ‘drm_name_info_wrap’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:479: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:479: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:479: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:479: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:480: warning: braces around scalar initializer
/usr/src/modules/fglrx/firegl_public.c:480: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:480: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c:480: error: ‘drm_mem_info_wrap’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:480: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:480: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:480: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:480: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:480: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:480: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:481: warning: braces around scalar initializer
/usr/src/modules/fglrx/firegl_public.c:481: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:481: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c:481: error: ‘drm_mem_info1_wrap’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:481: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:481: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:481: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:481: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:481: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:481: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:482: warning: braces around scalar initializer
/usr/src/modules/fglrx/firegl_public.c:482: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:482: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c:482: error: ‘drm_vm_info_wrap’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:482: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:482: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:482: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:482: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:482: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:482: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:483: warning: braces around scalar initializer
/usr/src/modules/fglrx/firegl_public.c:483: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:483: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c:483: error: ‘drm_clients_info_wrap’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:483: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:483: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:483: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:483: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:483: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:483: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:484: warning: braces around scalar initializer
/usr/src/modules/fglrx/firegl_public.c:484: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:484: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c:484: error: ‘firegl_lock_info_wrap’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:484: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:484: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:484: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:484: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:484: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:484: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:485: warning: braces around scalar initializer
/usr/src/modules/fglrx/firegl_public.c:485: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:485: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c:485: error: ‘firegl_umm_info_wrap’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:485: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:485: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:485: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:485: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:485: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:485: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:490: warning: braces around scalar initializer
/usr/src/modules/fglrx/firegl_public.c:490: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:490: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c:490: error: ‘firegl_bios_version_wrap’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:490: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:490: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:490: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:490: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:490: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:490: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:491: warning: braces around scalar initializer
/usr/src/modules/fglrx/firegl_public.c:491: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:491: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c:491: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:491: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:491: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:491: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:491: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:491: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:492: warning: braces around scalar initializer
/usr/src/modules/fglrx/firegl_public.c:492: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:492: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c:492: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:492: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:492: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:492: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:492: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:492: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:495: error: expected ‘)’ before ‘*’ token
/usr/src/modules/fglrx/firegl_public.c:560: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:584: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:608: error: storage class specified for parameter ‘firegl_stub_fops’
/usr/src/modules/fglrx/firegl_public.c:608: error: parameter ‘firegl_stub_fops’ is initialized
/usr/src/modules/fglrx/firegl_public.c:610: error: ‘firegl_stub_open’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:613: error: expected declaration specifiers or ‘...’ before ‘device_t’
/usr/src/modules/fglrx/firegl_public.c:614: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:633: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:650: error: expected declaration specifiers or ‘...’ before ‘device_t’
/usr/src/modules/fglrx/firegl_public.c:651: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:685: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:694: error: storage class specified for parameter ‘fglrx_pci_table’
/usr/src/modules/fglrx/firegl_public.c:694: error: parameter ‘fglrx_pci_table’ is initialized
/usr/src/modules/fglrx/firegl_public.c:696: warning: braces around scalar initializer
/usr/src/modules/fglrx/firegl_public.c:696: warning: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:697: error: field name not in record or union initializer
/usr/src/modules/fglrx/firegl_public.c:697: error: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:697: warning: initialization makes pointer from integer without a cast
/usr/src/modules/fglrx/firegl_public.c:698: error: field name not in record or union initializer
/usr/src/modules/fglrx/firegl_public.c:698: error: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:698: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:698: warning: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:699: error: field name not in record or union initializer
/usr/src/modules/fglrx/firegl_public.c:699: error: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:699: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:699: warning: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:700: error: field name not in record or union initializer
/usr/src/modules/fglrx/firegl_public.c:700: error: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:700: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:700: warning: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:701: error: field name not in record or union initializer
/usr/src/modules/fglrx/firegl_public.c:701: error: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:701: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:701: warning: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:702: error: field name not in record or union initializer
/usr/src/modules/fglrx/firegl_public.c:702: error: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:702: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:702: warning: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:704: warning: braces around scalar initializer
/usr/src/modules/fglrx/firegl_public.c:704: warning: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:704: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:704: warning: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:708: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:722: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:765: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:799: error: storage class specified for parameter ‘fglrx_pci_driver’
/usr/src/modules/fglrx/firegl_public.c:799: error: parameter ‘fglrx_pci_driver’ is initialized
/usr/src/modules/fglrx/firegl_public.c:803: error: ‘fglrx_pci_probe’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:805: error: ‘fglrx_pci_suspend’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:806: error: ‘fglrx_pci_resume’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:815: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:904: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:934: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:934: error: ‘init_module’ defined both normally and as an alias
/usr/src/modules/fglrx/firegl_public.c:934: error: expected declaration specifiers before ‘;’ token
/usr/src/modules/fglrx/firegl_public.c:935: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:935: error: ‘cleanup_module’ defined both normally and as an alias
/usr/src/modules/fglrx/firegl_public.c:935: error: expected declaration specifiers before ‘;’ token
/usr/src/modules/fglrx/firegl_public.c:941: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:954: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:960: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:968: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:974: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:979: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1003: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1010: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1015: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1020: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1026: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1032: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1038: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1043: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1048: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1053: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1063: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1068: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1073: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1114: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1126: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1131: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1138: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1149: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1154: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1163: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1168: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1173: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1178: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1183: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1188: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1195: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1200: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1207: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1212: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1248: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1253: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1261: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1266: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1271: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1276: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1285: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1306: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1402: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1411: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1422: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1427: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1432: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1437: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1442: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1447: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1454: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1459: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1464: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1469: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1474: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1479: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1484: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1491: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1496: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1501: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1506: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1516: error: storage class specified for parameter ‘PFNMLOCK’
/usr/src/modules/fglrx/firegl_public.c:1517: error: storage class specified for parameter ‘PFNMUNLOCK’
/usr/src/modules/fglrx/firegl_public.c:1521: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1536: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1551: error: storage class specified for parameter ‘PFNMODIFYLDT’
/usr/src/modules/fglrx/firegl_public.c:1554: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1575: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1580: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1587: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1696: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1712: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1728: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1733: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1738: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1763: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1768: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1773: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1782: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1794: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1814: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1825: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1830: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1835: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1840: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1845: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1850: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1854: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1858: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1863: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1868: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1873: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1878: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1883: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1888: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1893: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1898: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1903: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1912: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1927: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1941: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1966: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1972: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1977: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2007: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2041: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2063: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2077: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2086: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2095: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2101: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2107: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2119: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2124: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2129: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2134: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2139: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2144: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2149: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2154: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2174: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2206: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2221: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2298: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2321: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2326: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2331: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2336: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2341: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2346: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2351: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2356: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2361: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2372: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2385: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2390: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2395: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2400: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2405: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2410: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2415: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2440: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2476: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2485: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2494: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2503: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token

---

### Post by lsutiger on 2007-06-01
And the end of the log:

/usr/src/modules/fglrx/firegl_public.c:2535: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2540: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2545: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2550: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2555: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2560: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2565: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2570: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2576: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2581: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2586: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2591: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2599: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2604: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2609: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2614: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2619: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2624: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2629: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2637: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2642: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2661: error: storage class specified for parameter ‘irq_handler_func’
/usr/src/modules/fglrx/firegl_public.c:2664: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2672: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2680: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2708: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2714: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2731: error: storage class specified for parameter ‘mem_map_t’
/usr/src/modules/fglrx/firegl_public.c:2732: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/src/modules/fglrx/firegl_public.c:2737: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘do_vm_nopage’
/usr/src/modules/fglrx/firegl_public.c:2773: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘do_vm_shm_nopage’
/usr/src/modules/fglrx/firegl_public.c:2859: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘do_vm_dma_nopage’
/usr/src/modules/fglrx/firegl_public.c:2899: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘do_vm_kmap_nopage’
/usr/src/modules/fglrx/firegl_public.c:2937: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘do_vm_pcie_nopage’
/usr/src/modules/fglrx/firegl_public.c:2989: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘do_vm_gart_nopage’
/usr/src/modules/fglrx/firegl_public.c:3012: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘vm_nopage’
/usr/src/modules/fglrx/firegl_public.c:3049: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘vm_shm_nopage’
/usr/src/modules/fglrx/firegl_public.c:3063: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘vm_dma_nopage’
/usr/src/modules/fglrx/firegl_public.c:3071: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘vm_kmap_nopage’
/usr/src/modules/fglrx/firegl_public.c:3079: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘vm_pcie_nopage’
/usr/src/modules/fglrx/firegl_public.c:3086: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘vm_gart_nopage’
/usr/src/modules/fglrx/firegl_public.c:3174: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3179: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3184: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3189: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3198: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3210: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3234: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3261: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3277: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3279: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3281: error: storage class specified for parameter ‘vm_ops’
/usr/src/modules/fglrx/firegl_public.c:3281: error: parameter ‘vm_ops’ is initialized
/usr/src/modules/fglrx/firegl_public.c:3283: error: ‘vm_nopage’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:3284: error: ‘ip_drm_vm_open’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:3285: error: ‘ip_drm_vm_close’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:3299: error: storage class specified for parameter ‘vm_shm_ops’
/usr/src/modules/fglrx/firegl_public.c:3299: error: parameter ‘vm_shm_ops’ is initialized
/usr/src/modules/fglrx/firegl_public.c:3301: error: ‘vm_shm_nopage’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:3306: error: storage class specified for parameter ‘vm_pci_bq_ops’
/usr/src/modules/fglrx/firegl_public.c:3306: error: parameter ‘vm_pci_bq_ops’ is initialized
/usr/src/modules/fglrx/firegl_public.c:3308: error: ‘vm_dma_nopage’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:3313: error: storage class specified for parameter ‘vm_ctx_ops’
/usr/src/modules/fglrx/firegl_public.c:3313: error: parameter ‘vm_ctx_ops’ is initialized
/usr/src/modules/fglrx/firegl_public.c:3320: error: storage class specified for parameter ‘vm_pcie_ops’
/usr/src/modules/fglrx/firegl_public.c:3320: error: parameter ‘vm_pcie_ops’ is initialized
/usr/src/modules/fglrx/firegl_public.c:3322: error: ‘vm_pcie_nopage’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:3327: error: storage class specified for parameter ‘vm_kmap_ops’
/usr/src/modules/fglrx/firegl_public.c:3327: error: parameter ‘vm_kmap_ops’ is initialized
/usr/src/modules/fglrx/firegl_public.c:3329: error: ‘vm_kmap_nopage’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:3334: error: storage class specified for parameter ‘vm_gart_ops’
/usr/src/modules/fglrx/firegl_public.c:3334: error: parameter ‘vm_gart_ops’ is initialized
/usr/src/modules/fglrx/firegl_public.c:3336: error: ‘vm_gart_nopage’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:3343: error: storage class specified for parameter ‘vm_agp_bq_ops’
/usr/src/modules/fglrx/firegl_public.c:3343: error: parameter ‘vm_agp_bq_ops’ is initialized
/usr/src/modules/fglrx/firegl_public.c:3363: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3549: error: parameter ‘__ke_agp_try_unsupported’ is initialized
/usr/src/modules/fglrx/firegl_public.c:3552: error: storage class specified for parameter ‘__fgl_agp_init’
/usr/src/modules/fglrx/firegl_public.c:3553: error: storage class specified for parameter ‘__fgl_agp_cleanup’
/usr/src/modules/fglrx/firegl_public.c:3554: error: storage class specified for parameter ‘__fgl_agp_try_unsupported’
/usr/src/modules/fglrx/firegl_public.c:3555: error: storage class specified for parameter ‘__fgl_agp_allocate_memory_phys_list’
/usr/src/modules/fglrx/firegl_public.c:3571: error: parameter ‘__ke_firegl_agpgart_inuse’ is initialized
/usr/src/modules/fglrx/firegl_public.c:3587: error: storage class specified for parameter ‘drm_agp_t’
/usr/src/modules/fglrx/firegl_public.c:3598: error: storage class specified for parameter ‘firegl_agp_bridge’
/usr/src/modules/fglrx/firegl_public.c:3598: error: parameter ‘firegl_agp_bridge’ is initialized
/usr/src/modules/fglrx/firegl_public.c:3599: error: storage class specified for parameter ‘firegl_pci_device’
/usr/src/modules/fglrx/firegl_public.c:3599: error: parameter ‘firegl_pci_device’ is initialized
/usr/src/modules/fglrx/firegl_public.c:3603: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3608: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3613: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3619: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3625: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3630: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘drm_agp’
/usr/src/modules/fglrx/firegl_public.c:3639: error: expected declaration specifiers before ‘;’ token
/usr/src/modules/fglrx/firegl_public.c:3680: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/src/modules/fglrx/firegl_public.c:3789: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3815: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3823: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3848: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3862: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3868: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3876: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token/usr/src/modules/fglrx/firegl_public.c:3884: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3892: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3901: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3932: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3943: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3949: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4015: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4021: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4092: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4108: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4114: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4125: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4146: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4233: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4275: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4298: error: parameter ‘FIREGL_PUBLIC_DBG_STATE’ is initialized
/usr/src/modules/fglrx/firegl_public.c:4324: error: storage class specified for parameter ‘kasContext_t’
/usr/src/modules/fglrx/firegl_public.c:4327: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘kasContext’
/usr/src/modules/fglrx/firegl_public.c:4342: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4359: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4374: error: expected declaration specifiers before ‘__attribute__’
/usr/src/modules/fglrx/firegl_public.c:4399: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4430: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4472: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4493: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4510: error: storage class specified for parameter ‘kas_spin_lock_info_t’
/usr/src/modules/fglrx/firegl_public.c:4518: error: storage class specified for parameter ‘kas_spin_unlock_info_t’
/usr/src/modules/fglrx/firegl_public.c:4527: error: expected ‘)’ before ‘*’ token
/usr/src/modules/fglrx/firegl_public.c:4593: error: expected ‘)’ before ‘*’ token
/usr/src/modules/fglrx/firegl_public.c:4627: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4649: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4674: error: storage class specified for parameter ‘kasIdhRoutine_t’
/usr/src/modules/fglrx/firegl_public.c:4680: error: expected specifier-qualifier-list before ‘kasIdhRoutine_t’
/usr/src/modules/fglrx/firegl_public.c:4682: error: storage class specified for parameter ‘kasIdh_t’
/usr/src/modules/fglrx/firegl_public.c:4699: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4720: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4740: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4758: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4767: error: storage class specified for parameter ‘kasSyncRoutine_t’
/usr/src/modules/fglrx/firegl_public.c:4788: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4836: error: storage class specified for parameter ‘kasSpinlock_t’
/usr/src/modules/fglrx/firegl_public.c:4844: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4862: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4880: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4907: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4930: warning: ‘kmem_cache_t’ is deprecated
/usr/src/modules/fglrx/firegl_public.c:4934: error: storage class specified for parameter ‘kasSlabCache_t’
/usr/src/modules/fglrx/firegl_public.c:4942: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4963: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:4993: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5030: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5095: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5134: error: storage class specified for parameter ‘kasEvent_t’
/usr/src/modules/fglrx/firegl_public.c:5142: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5158: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5177: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5194: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5220: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5332: error: storage class specified for parameter ‘kasMutex_t’
/usr/src/modules/fglrx/firegl_public.c:5340: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5352: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5372: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5417: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5445: error: storage class specified for parameter ‘KAS_ThreadRoutine_t’
/usr/src/modules/fglrx/firegl_public.c:5452: error: expected specifier-qualifier-list before ‘KAS_ThreadRoutine_t’
/usr/src/modules/fglrx/firegl_public.c:5454: error: storage class specified for parameter ‘kasThread_t’
/usr/src/modules/fglrx/firegl_public.c:5464: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5480: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5500: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5523: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5541: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5556: error: storage class specified for parameter ‘kasInterlockedListHead_t’
/usr/src/modules/fglrx/firegl_public.c:5562: error: storage class specified for parameter ‘kasInterlockedListEntry_t’
/usr/src/modules/fglrx/firegl_public.c:5570: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5584: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5601: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5624: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5685: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5744: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5804: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5824: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5860: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5900: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5942: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5962: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5978: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5987: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:5989: error: old-style parameter declarations in prototyped function definition
/usr/src/modules/fglrx/firegl_public.c:208: error: parameter name omitted
/usr/src/modules/fglrx/firegl_public.c:208: error: parameter name omitted
/usr/src/modules/fglrx/firegl_public.c:208: error: parameter name omitted
/usr/src/modules/fglrx/firegl_public.c:5989: error: expected ‘{’ at end of input
make[2]: *** [/usr/src/modules/fglrx/firegl_public.o] Error 1
make[1]: *** [_module_/usr/src/modules/fglrx] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [build] Error 2

---

