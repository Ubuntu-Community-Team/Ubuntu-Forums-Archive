---
title: "problem with scim"
date: 2008-08-28
forum: Desktop Environments
---

### Post by samuelandjw on 2008-08-28
I use Ubuntu 8.04 and I have problem with scim. 

At first, I installed several scim packages. But when I attempted to trigger the input method using control+space after an restart, nothing happened. I have attempted to launch scim using scim -d, only to get the following error messages:
Smart Common Input Method 1.4.7

Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
Failed to launch SCIM.

Having seen this article: [https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)
I installed all the packages needed through language support panel. Unfortunately, this problem remains.

relevant system log is as following:
Aug 28 00:06:16 wdg-laptop syslogd 1.5.0#1ubuntu1: restart.
Aug 28 00:06:54 wdg-laptop kernel: [  681.941241] scim-launcher[8066]: segfault at b7b7de6c eip b7b7de6c esp bfa0c4cc error 4
Aug 28 00:13:26 wdg-laptop kernel: [ 1073.960204] scim-launcher[13278]: segfault at b7b58e6c eip b7b58e6c esp bf9e54ac error 4
Aug 28 00:13:36 wdg-laptop kernel: [ 1083.320241] scim-launcher[13722]: segfault at b7b41e6c eip b7b41e6c esp bf83cafc error 4

thank you.

---

### Post by Pinong on 2008-11-07
I got the same problem, it seemed crashed when load scim-pinyin module

---

