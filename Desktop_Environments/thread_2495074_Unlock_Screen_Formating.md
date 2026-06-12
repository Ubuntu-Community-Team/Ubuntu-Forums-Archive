---
title: "Unlock Screen Formating"
date: 2024-02-06
forum: Desktop Environments
---

### Post by hei17 on 2024-02-06
I have created a mytheme in Ubuntu 22.04, gnome 42.9, 64bit. On a Dell Latitude E6410 laptop. The gnome-shell.css file in mytheme has this formatting for unlocking the laptop.
```
.login-dialog,
.unlock-dialog {
  border: none;
  background-image: url("zbeach.jpg");
  color: #ff0000; }
  .login-dialog .modal-dialog-button-box,
  .unlock-dialog .modal-dialog-button-box {
    spacing: 3px; }
  .login-dialog .modal-dialog-button,
  .unlock-dialog .modal-dialog-button {
    padding: 4px 18px;
    box-shadow: 0 1px 3px transparent;
    background-color: #ffff00;
    border-color: #00ff00;
    color: #0000ff; }
      .login-dialog .modal-dialog-button:hover,
    .unlock-dialog .modal-dialog-button:hover {
      background-color: #ffff00; }
    .login-dialog .modal-dialog-button:focus,
    .unlock-dialog .modal-dialog-button:focus {
      border-color: #00ff00;
      box-shadow: inset 0 0 0 1px transparent; }
    .login-dialog .modal-dialog-button:active,
    .unlock-dialog .modal-dialog-button:active {
      box-shadow: none;
      background-color: #ffff00;
      color: #0000ff; }
    .login-dialog .modal-dialog-button:default,
    .unlock-dialog .modal-dialog-button:default {
      background-color: #ffff00;
      color: #0000ff; }
      .login-dialog .modal-dialog-button:default:focus,
      .unlock-dialog .modal-dialog-button:default:focus {
        box-shadow: inset 0 0 0 2px transparent; }
      .login-dialog .modal-dialog-button:default:hover, .login-dialog .modal-dialog-button:default:focus,
      .unlock-dialog .modal-dialog-button:default:hover,
      .unlock-dialog .modal-dialog-button:default:focus {
        background-color: #ffff00;
        color: blue; }
      .login-dialog .modal-dialog-button:default:active,
      .unlock-dialog .modal-dialog-button:default:active {
        background-color: #ffff00;
        color: #0000ff; }
      .login-dialog .modal-dialog-button:default:insensitive,
      .unlock-dialog .modal-dialog-button:default:insensitive {
        color: #0000ff;
        background-color: #ffff00;
        background-color: #ffff00;
        color: #0000ff; }
```
But when go to unlock the unlock screen it is not the formatting that appears. I enter my password and for a second the formatting above appears. My question is what script or program is superseding my theme formatting and where is it located so I can change it.
Any help would be appreciated.

---

### Post by umangwah67 on 2024-02-07
hey
i think you might need to  modify CSS rules for unlock screen. Trynna inspect unlock screen element using browser tool further more check any GNOME extension affecting styling of unlock screen.
thanks

---

