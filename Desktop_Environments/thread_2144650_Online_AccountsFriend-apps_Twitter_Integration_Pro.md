---
title: "Online Accounts/Friend-apps Twitter Integration Problem in 13.04"
date: 2013-05-13
forum: Desktop Environments
---

### Post by zero-Q on 2013-05-13
Hi,
After fresh install 13.04 I could not use my twitter account. Whenever I click to add button for twitter in online account, twitter authentication page doesnt come and after white screen it returns to Online accounts' main page.

Is there anything I can do or do I have to wait patch or something?

Here is commandline usage of online-accounts-preferences after trying twitter:

online-accounts-preferences



aaaa@bbbbb-pc:~$ online-accounts-preferences
credentials-cc-panel-Message: cc-credentials-accounts-model.vala:349: Failure change reported for non-existent account ID: 0
credentials-cc-panel-Message: cc-credentials-account-applications-model.vala:156: No valid plugin found for application 'unity-scope-gdrive' with account '1'
credentials-cc-panel-Message: cc-credentials-account-applications-model.vala:156: No valid plugin found for application 'shotwell' with account '1'
credentials-cc-panel-Message: cc-credentials-account-applications-model.vala:156: No valid plugin found for application 'unity-lens-photos' with account '1'

(gnome-control-center:19370): account-plugin-WARNING **: AuthSession error: GDBus.Error:com.google.code.AccountsSSO.SingleSignOn.Error.Ssl: The issuer certificate of a locally looked up certificate could not be found;The root CA certificate is not trusted for this purpose;

(gnome-control-center:19370): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed

(gnome-control-center:19370): GLib-CRITICAL **: g_variant_ref_sink: assertion `value != NULL' failed

(gnome-control-center:19370): GLib-CRITICAL **: g_variant_new_variant: assertion `value != NULL' failed

(gnome-control-center:19370): GLib-CRITICAL **: g_variant_get_type: assertion `value != NULL' failed

(gnome-control-center:19370): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion `g_variant_type_check (type)' failed

(gnome-control-center:19370): GLib-CRITICAL **: g_variant_builder_add_value: assertion `!GVSB(builder)->expected_type || g_variant_is_of_type (value, GVSB(builder)->expected_type)' failed

(gnome-control-center:19370): GLib-CRITICAL **: g_variant_builder_end: assertion `GVSB(builder)->offset >= GVSB(builder)->min_items' failed

(gnome-control-center:19370): GLib-CRITICAL **: g_variant_get_type: assertion `value != NULL' failed

(gnome-control-center:19370): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion `g_variant_type_check (type)' failed

(gnome-control-center:19370): GLib-CRITICAL **: g_variant_builder_add_value: assertion `!GVSB(builder)->expected_type || g_variant_is_of_type (value, GVSB(builder)->expected_type)' failed

(gnome-control-center:19370): credentials-cc-panel-CRITICAL **: cc-credentials-authorization-page.vala:196: Error completing auth session process: GDBus.Error:com.google.code.AccountsSSO.SingleSignOn.Error.Ssl: The issuer certificate of a locally looked up certificate could not be found;The root CA certificate is not trusted for this purpose;
credentials-cc-panel-Message: cc-credentials-accounts-model.vala:349: Failure change reported for non-existent account ID: 0

---

