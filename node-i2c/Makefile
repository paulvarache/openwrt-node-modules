##############################################
# OpenWrt Makefile for node-i2c program
#
# Be very careful of spacing in this file.
# Indents should be tabs, not spaces, and
# there should be no trailing whitespace in
# lines that are not commented.
#
##############################################

include $(TOPDIR)/rules.mk

# Name and release number of this package
PKG_NAME:=node-i2c
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=0.10
PKG_SOURCE_URL:=https://github.com/paulvarache/node-i2c.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)
PKG_SOURCE:=$(PKG_NAME).tar.gz
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)
PKG_INSTALL:=1

export npm_config_arch=mips

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
	SECTION:=utils
	CATEGORY:=Utilities
	SUBMENU:=Utilities
	TITLE:=Node module for accessing I2C devices
endef

define Package/$(PKG_NAME)/compile
	$(MAKE) -e -C $(PKG_BUILD_DIR)
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/lib/node_modules
	$(INSTALL_DIR) $(1)/usr/lib/node_modules/node-i2c
	$(CP) $(PKG_BUILD_DIR)/main.js $(1)/usr/lib/node_modules/node-i2c/
	$(CP) $(PKG_BUILD_DIR)/package.json $(1)/usr/lib/node_modules/node-i2c/
	$(CP) -r $(PKG_BUILD_DIR)/lib $(1)/usr/lib/node_modules/node-i2c/
	$(CP) -r $(PKG_BUILD_DIR)/build $(1)/usr/lib/node_modules/node-i2c/
endef

# Start
$(eval $(call BuildPackage,$(PKG_NAME)))
