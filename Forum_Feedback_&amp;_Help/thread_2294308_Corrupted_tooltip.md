---
title: "Corrupted tooltip"
date: 2015-09-10
forum: Forum Feedback &amp; Help
---

### Post by cariboo on 2015-09-10
I'm running Wily, with Chromium Version 44.0.2403.89 Ubuntu 15.10 (64-bit). I seem to be getting corrupted tooltips, the screenshot isn't as bad as some I've seen, but his is what I'm seeing.

---

### Post by flocculant on 2015-09-10
Can confirm that. 

Don't use chromium for anything other than BBC pages - flash problems ... 

Consequently the chromium is as installed - no extensions in use at all.

---

### Post by tgalati4 on 2015-09-10
I'm running nearly the same version of Chrome (44.0.2403.157) on 14.04 and I've never seen that.  Try *firefox* and see if you get the same behavior.  It looks like a compositing issue or perhaps a GPU/video RAM issue.  The fact that it is not quite repeatable--some tooltips are more messed up than others could indicate a hardware issue.

What graphics are you running?

```
lspci | grep VGA
```

---

### Post by iulian X on 2015-09-10
Have you tried to enable or disable hardware acceleration?

---

### Post by cariboo on 2015-09-10
I only have the problem on my desktop system with a Nvidia Geforce 210 graphics adapter. I found a bug report, but it is for systems running an AMD graphics adapter.

```
lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)

```

---

### Post by tgalati4 on 2015-09-10
I would be curious to see the differences between Chrome and chromium:

```
ps aux | more
```

Cut and paste the chromium extensions.  MIne look like this for Chrome:

> 
tgalati4   747  0.0  3.8 896256 79128 ?        Sl   Sep08   0:59 /opt/google/chrome/chrome --type=renderer --enable-display-list-2d-canvas --enable-experimen
tal-canvas-features --enable-deferred-image-decoding --lang=en-US --force-fieldtrials=*AffiliationBasedMatching/Enabled/AudioProcessing48kHzSupport/Default/*
AutofillEnabled/Default/*AutofillFieldMetadata/Enabled/CaptivePortalInterstitial/Enabled/*ChildAccountDetection/Disabled/ChromeDashboard/Default/*DomRel-Enab
le/enable/*EnableSessionCrashedBubbleUI/Disabled/*EnhancedBookmarks/Default/*ExtensionContentVerification/Enforce/*ExtensionDeveloperModeWarning/Default/*Ext
ensionInstallVerification/None/*IconNTP/Default/*NewProfileManagement/Enabled/*NewVideoRendererTrial/Enabled/*OmniboxBundledExperimentV1/StableHQPFrequencyBu
gFix_PrePeriod_1/*PasswordGeneration/Disabled/PasswordLinkInSettings/Enabled/PermissionBubbleRollout/Enabled/*PrerenderFromOmnibox/OmniboxPrerenderEnabled/*Q
UIC/EnabledForLargePopulation/*RefreshTokenDeviceId/Enabled/*RememberCertificateErrorDecisions/Default/ReportCertificateErrors/ShowAndPossiblySend/ReportCert
ificateErrorsOverHttp/UploadReportsOverHttp/SHA1IdentityUIWarning/Enabled/SHA1ToolbarUIJanuary2016/Warning/SHA1ToolbarUIJanuary2017/Error/*SafeBrowsingIncide
ntReportingService/Default/*SdchPersistence/Default/SessionRestoreBackgroundLoading/Restore/*SettingsEnforcement/no_enforcement/*SyncBackingDatabase32K/Enabl
ed/*UMA-Dynamic-Binary-Uniformity-Trial/default/*UMA-Population-Restrict/normal/*UMA-Uniformity-Trial-1-Percent/group_66/*UMA-Uniformity-Trial-10-Percent/gro
up_03/*UMA-Uniformity-Trial-100-Percent/group_01/*UMA-Uniformity-Trial-20-Percent/group_01/*UMA-Uniformity-Trial-5-Percent/default/*UMA-Uniformity-Trial-50-P
ercent/group_01/*UseDelayAgnosticAEC

I have all of the experimental hardware rendering turned on.  But I'm running Intel graphics with the open driver. And that needs all the help it can get!

---

### Post by flocculant on 2015-09-11
> **cariboo said:**
> I only have the problem on my desktop system with a Nvidia Geforce 210 graphics adapter. I found a bug report, but it is for systems running an AMD graphics adapter.

```
lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)

```

01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)

---

