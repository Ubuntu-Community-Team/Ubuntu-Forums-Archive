---
title: "openwengo 2.0"
date: 2006-08-15
forum: Desktop Environments
---

### Post by otacan on 2006-08-15
I tried to use openwengo version 2.0 but I had this error:
> 
(debug) 19:33:30 bool NetworkDiscovery::testHTTP(const std::string&, bool): cannot connect to ws.wengo.fr:443/softphone-sso/sso2.php with SSL
* About to connect() to ws.wengo.fr port 80
* Connection time-out
* Closing connection #0
* a timeout was reached
(debug) 19:33:40 bool NetworkDiscovery::testHTTP(const std::string&, bool): cannot connect to ws.wengo.fr:80/softphone-sso/sso2.php without SSL
(debug) 19:33:40 bool WengoAccount::discoverForSSO(): SSO cannot connect
(debug) 19:33:40 EnumSipLoginState::SipLoginState WengoAccount::discoverNetwork(): error while discovering network for SSO




I have both lib libssl0.9.7 and libssl0.9.8
and I dont have any firewall or proxy

thanks for Help

---

