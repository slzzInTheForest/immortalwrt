include $(TOPDIR)/rules.mk

PKG_NAME:=r8126
PKG_VERSION:=10.013.00
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=https://github.com/Noltari/rtl8126/releases/download/$(PKG_VERSION)
PKG_HASH:=b41bda6ff3bbb7d9bc5b81c5c21355f031587d3a3a5862abcd4d766e942272e7

PKG_BUILD_PARALLEL:=1
PKG_LICENSE:=GPL-2.0-only
PKG_MAINTAINER:=Alvaro Fernandez Rojas <noltari@gmail.com>

include $(INCLUDE_DIR)/kernel.mk
include $(INCLUDE_DIR)/package.mk

define KernelPackage/r8126
  SUBMENU:=Network Devices
  TITLE:=Realtek RTL8126 PCI 5 Gigabit Ethernet driver
  DEPENDS:=@PCI_SUPPORT
  FILES:=$(PKG_BUILD_DIR)/src/r8126.ko
  AUTOLOAD:=$(call AutoProbe,r8126)
  PROVIDES:=kmod-r8169
endef

define KernelPackage/r8126/description
  This package contains a driver for Realtek r8126 chipsets.
endef

define Build/Compile
	+$(KERNEL_MAKE) $(PKG_JOBS) \
		M=$(PKG_BUILD_DIR)/src \
		CONFIG_ASPM=n \
		ENABLE_RSS_SUPPORT=y \
		modules
endef

$(eval $(call KernelPackage,r8126))
