---
# required metadata

title: Add VPN settings to devices in Microsoft Intune - Azure | Microsoft Docs
description: On Android device administrator, Android Enterprise, iOS, iPadOS, macOS, and Windows devices, use built-in settings to create virtual private network (VPN) connections in Microsoft Intune.
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/14/2021
ms.topic: how-to
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology:

# optional metadata

#ROBOTS:
#audience:
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# Create VPN profiles to connect to VPN servers in Intune

Virtual private networks (VPNs) give users secure remote access to your organization network. Devices use a VPN connection profile to start a connection with the VPN server. **VPN profiles** in Microsoft Intune assign VPN settings to users and devices in your organization. Use these settings so users can easily and securely connect to your organizational network.

This feature applies to:

- Android device administrator
- Android Enterprise personally-owned devices with a work profile
- iOS/iPadOS
- macOS
- Windows 10 and newer
- Windows 8.1 and newer

For example, you want to configure all iOS/iPadOS devices with the required settings to connect to a file share on the organization network. You create a VPN profile that includes these settings. You assign this profile to all users who have iOS/iPadOS devices. The users see the VPN connection in the list of available networks, and can connect with minimal effort.

This article lists the VPN apps you can use, shows you how to create a VPN profile, and includes guidance on securing your VPN profiles. You must deploy the VPN app before you create the VPN profile. If you need help deploying apps using Microsoft Intune, see [What is app management in Microsoft Intune?](../apps/app-management.md).

> [!TIP]
> *VPN* profiles for a device tunnel are supported for [Windows 10 Enterprise multi-session remote desktops](../fundamentals/azure-virtual-desktop-multi-session.md).

> [!NOTE]
>
> - User enrollment for iOS/iPadOS and macOS only supports [per-app VPN](vpn-setting-configure-per-app.md).
> - You can use [Intune custom configuration policies](custom-settings-configure.md) to create VPN profiles for the following platforms:
>
>   - Android 4 and later
>   - Enrolled devices that run Windows 8.1 and later
>   - Enrolled devices that run Windows 10 desktop
>   - Windows Holographic for Business

## VPN connection types

> [!IMPORTANT]
> Before you can use VPN profiles assigned to a device, you must install the VPN app for the profile. To help you assign the app using Intune, see [Add apps to Microsoft Intune](../apps/apps-add.md).  

You can create VPN profiles using the following connection types:

- Automatic
  - Windows 10

- Check Point Capsule VPN
  - Android device administrator
  - Android Enterprise personally owned devices with a work profile
  - Android Enterprise fully managed and corporate-owned work profile: Use [app configuration policy](../apps/app-configuration-vpn-ae.md)
  - iOS/iPadOS
  - macOS
  - Windows 10
  - Windows 8.1

- Cisco AnyConnect
  - Android device administrator
  - Android Enterprise personally owned devices with a work profile
  - Android Enterprise fully managed and corporate-owned work profile
  - iOS/iPadOS
  - macOS
  - Windows 10

- Cisco (IPSec)
  - iOS/iPadOS

- Citrix SSO
  - Android device administrator
  - Android Enterprise personally owned devices with a work profile: Use [app configuration policy](../apps/app-configuration-vpn-ae.md)
  - Android Enterprise fully managed and corporate-owned work profiles: Use [app configuration policy](../apps/app-configuration-vpn-ae.md)
  - iOS/iPadOS
  - Windows 10

- Custom VPN
  - iOS/iPadOS
  - macOS

  Create custom VPN profiles using URI settings in [Create a profile with custom settings](custom-settings-configure.md).

- F5 Access
  - Android device administrator
  - Android Enterprise personally owned devices with a work profile
  - Android Enterprise fully managed and corporate-owned work profile
  - iOS/iPadOS
  - macOS
  - Windows 10
  - Windows 8.1

- IKEv2
  - iOS/iPadOS
  - Windows 10

- L2TP
  - Windows 10

- Microsoft Tunnel (standalone client)
  - iOS/iPadOS  

- Microsoft Tunnel  
  - Android Enterprise personally owned devices with a work profile
  - Android Enterprise fully managed and corporate-owned work profile

  > [!Important]
  > Prior to support for using Microsoft Defender for Endpoint as the tunnel client app, a standalone tunnel client app was available in preview and used a connection type of **Microsoft Tunnel (standalone client)**. As of June 14, 2021, both the standalone tunnel app and standalone client connection type are deprecated and drop from support 60 days later after August 14, 2021.

- NetMotion Mobility
  - Android Enterprise personally owned devices with a work profile
  - Android Enterprise fully managed and corporate-owned work profile
  - iOS/iPadOS
  - macOS

- Palo Alto Networks GlobalProtect
  - Android Enterprise personally owned devices with a work profile: Use [app configuration policy](../apps/app-configuration-vpn-ae.md)
  - Android Enterprise fully managed and corporate-owned work profile: Use [app configuration policy](../apps/app-configuration-vpn-ae.md)
  - iOS/iPadOS
  - Windows 10

- PPTP
  - Windows 10

- Pulse Secure
  - Android device administrator
  - Android Enterprise personally owned devices with a work profile
  - Android Enterprise fully managed and corporate-owned work profile
  - iOS/iPadOS
  - Windows 10
  - Windows 8.1

- SonicWall Mobile Connect
  - Android device administrator
  - Android Enterprise personally owned devices with a work profile
  - Android Enterprise fully managed and corporate-owned work profile
  - iOS/iPadOS
  - macOS
  - Windows 10
  - Windows 8.1

- Zscaler
  - Android Enterprise personally owned devices with a work profile: Use [app configuration policy](../apps/app-configuration-vpn-ae.md)
  - Android Enterprise fully managed and corporate-owned work profile: Use [app configuration policy](../apps/app-configuration-vpn-ae.md)
  - iOS/iPadOS

## Create the profile

1. Sign in to the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Configuration profiles** > **Create profile**.
3. Enter the following properties:

    - **Platform**: Choose the platform of your devices. Your options:
      - **Android device administrator**
      - **Android Enterprise** > **Fully Managed, Dedicated, and Corporate-Owned Work Profile**
      - **Android Enterprise** > **Personally-owned work profile**
      - **iOS/iPadOS**
      - **macOS**
      - **Windows 10 and later**
      - **Windows 8.1 and later**
    - **Profile**: Select **VPN**. Or, select **Templates** > **VPN**.

4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the profile. Name your profiles so you can easily identify them later. For example, a good profile name is **VPN profile for entire company**.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.

6. Select **Next**.
7. In **Configuration settings**, depending on the platform you chose, the settings you can configure are different. Select your platform for detailed settings:

    - [Android device administrator](vpn-settings-android.md)
    - [Android Enterprise](vpn-settings-android-enterprise.md)
    - [iOS/iPadOS](vpn-settings-ios.md)
    - [macOS](vpn-settings-macos.md)
    - [Windows 10](vpn-settings-windows-10.md) (including Windows Holographic for Business)
    - [Windows 8.1](vpn-settings-windows-8-1.md)

8. Select **Next**.
9. In **Scope tags** (optional), assign a tag to filter the profile to specific IT groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. For more information about scope tags, see [Use RBAC and scope tags for distributed IT](../fundamentals/scope-tags.md).

    Select **Next**.

10. In **Assignments**, select the user or groups that will receive your profile. For more information on assigning profiles, see [Assign user and device profiles](device-profile-assign.md).

    Select **Next**.

11. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.

## Secure your VPN profiles

VPN profiles can use many different connection types and protocols from different manufacturers. These connections are typically secured through the following methods.

### Certificates

When you create the VPN profile, you choose a SCEP or PKCS certificate profile that you previously created in Intune. This profile is known as the identity certificate. It's used to authenticate against a trusted certificate profile (or *root certificate*) that you create to allow the user's device to connect. The trusted certificate is assigned to the computer that authenticates the VPN connection, typically, the VPN server.

If you use certificate-based authentication for your VPN profile, then deploy the VPN profile, certificate profile, and trusted root profile to the same groups. This assignment makes sure each device recognizes the legitimacy of your certificate authority.

For more information about how to create and use certificate profiles in Intune, see [How to configure certificates with Microsoft Intune](../protect/certificates-configure.md).

> [!NOTE]
> Certificates added using the **PKCS imported certificate** profile aren't supported for VPN authentication. Certificates added using the **PKCS certificates** profile are supported for VPN authentication.

### User name and password

The user authenticates to the VPN server by providing a user name and password, or [derived credentials](../protect/derived-credentials.md).

## Next steps

- [Assign the profile](device-profile-assign.md) and [monitor its status](device-profile-monitor.md).
- You can also create and use per-app VPNs on [Android device administrator/Android Enterprise](android-pulse-secure-per-app-vpn.md) and [iOS/iPadOS](vpn-setting-configure-per-app.md) devices.
