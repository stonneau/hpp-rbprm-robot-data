# Copyright (c) 2012 CNRS
# Author: Florent Lamiraux
#
# This file is part of hpp-rbprm-corba.
# hpp-rbprm-corba is free software: you can redistribute it
# and/or modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation, either version
# 3 of the License, or (at your option) any later version.
#
# hpp-rbprm-corba is distributed in the hope that it will be
# useful, but WITHOUT ANY WARRANTY; without even the implied warranty
# of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# General Lesser Public License for more details.  You should have
# received a copy of the GNU Lesser General Public License along with
# hpp-rbprm-corba.  If not, see
# <http://www.gnu.org/licenses/>.

# Requires at least CMake 2.6 to configure the package.
CMAKE_MINIMUM_REQUIRED(VERSION 2.6)

SET(CXX_DISABLE_WERROR true)

INCLUDE(cmake/base.cmake)
INCLUDE(cmake/idl.cmake)
INCLUDE(cmake/python.cmake)

SET(PROJECT_NAME hpp-rbprm-robot-data)
SET(PROJECT_DESCRIPTION "Database for robots using hpp-rbprm")
SET(PROJECT_URL "")

SETUP_PROJECT ()

# search for python
FINDPYTHON(2.7 EXACT REQUIRED)

PKG_CONFIG_APPEND_LIBS(${PROJECT_NAME})

SET(CATKIN_PACKAGE_SHARE_DESTINATION
  ${CMAKE_INSTALL_DATAROOTDIR}/${PROJECT_NAME})
  
  
SET(CATKIN_HYQ_PACKAGE_SHARE_DESTINATION
  ${CMAKE_INSTALL_DATAROOTDIR}/hyq-rbprm)
  
install(FILES
  data/hyq/package.xml
  DESTINATION ${CATKIN_HYQ_PACKAGE_SHARE_DESTINATION}
  )
  
install(FILES
  data/hyq/urdf/hyq_trunk.urdf
  data/hyq/urdf/hyq_trunk_large.urdf
  data/hyq/urdf/hyq_rhleg_rom.urdf
  data/hyq/urdf/hyq_rfleg_rom.urdf
  data/hyq/urdf/hyq_lhleg_rom.urdf
  data/hyq/urdf/hyq_lfleg_rom.urdf
  data/hyq/urdf/hyq_rom.urdf
  DESTINATION ${CATKIN_HYQ_PACKAGE_SHARE_DESTINATION}/urdf
  )
  
  
install(FILES
  data/hyq/srdf/hyq_trunk.srdf
  data/hyq/srdf/hyq_trunk_large.srdf
  data/hyq/srdf/hyq_rhleg_rom.srdf
  data/hyq/srdf/hyq_rfleg_rom.srdf
  data/hyq/srdf/hyq_lhleg_rom.srdf
  data/hyq/srdf/hyq_lfleg_rom.srdf
  data/hyq/srdf/hyq_rom.srdf
  DESTINATION ${CATKIN_HYQ_PACKAGE_SHARE_DESTINATION}/srdf
  )
install(FILES
	data/hyq/meshes/hyq_all.stl
	data/hyq/meshes/hyq_trunk.stl
	data/hyq/meshes/hyq_trunk_large.stl
	data/hyq/meshes/hyq_rom.stl
	data/hyq/meshes/hyq_rhleg_rom.stl
	data/hyq/meshes/hyq_rfleg_rom.stl
	data/hyq/meshes/hyq_lhleg_rom.stl
	data/hyq/meshes/hyq_lfleg_rom.stl
  DESTINATION ${CATKIN_HYQ_PACKAGE_SHARE_DESTINATION}/meshes
  )
install(FILES
        data/hyq/database/hyq_rfleg.db
        data/hyq/database/hyq_lhleg.db
        data/hyq/database/hyq_rhleg.db
        data/hyq/database/hyq_lfleg.db
  DESTINATION ${CATKIN_HYQ_PACKAGE_SHARE_DESTINATION}/database
  )

install(FILES
        data/hyq/com_inequalities/__init__.py
        DESTINATION ${PYTHON_SITELIB}/hpp/corbaserver/rbprm/data/
)

install(FILES
        data/hyq/com_inequalities/__init__.py
        DESTINATION ${PYTHON_SITELIB}/hpp/corbaserver/rbprm/data/com_inequalities/
)


install(FILES
        data/hyq/com_inequalities/__init__.py
        data/hyq/com_inequalities/lfleg_com.ineq
        data/hyq/com_inequalities/lhleg_com.ineq
        data/hyq/com_inequalities/rhleg_com.ineq
        data/hyq/com_inequalities/rfleg_com.ineq
        DESTINATION ${PYTHON_SITELIB}/hpp/corbaserver/rbprm/data/com_inequalities/hyq
)


install(FILES
        data/hyq/com_inequalities/__init__.py
        data/spiderman/com_inequalities/LA_com.ineq
        data/spiderman/com_inequalities/LL_com.ineq
        data/spiderman/com_inequalities/RA_com.ineq
        data/spiderman/com_inequalities/RL_com.ineq
        DESTINATION ${PYTHON_SITELIB}/hpp/corbaserver/rbprm/data/com_inequalities/spiderman
)

SETUP_PROJECT_FINALIZE()
