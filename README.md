# Real_State

##################### LOGIN API (ONLY TOKEN) #######################

#1. phython3 -m venv real_state_venv

#2 source real_state_venv/bin/activate

#3. pip3 install django djangorestframework djangorestframework-simplejwt

#4. check install django: django-admin

#5. django-admin startproject RealState .

#6. check run: python3 manage.py migrate after that python3 manage.py runserver

#7. inside the configuration settings.py real state folder:

from pathlib import Path

import os

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'rest_framework'
]

TIME_ZONE = 'Asia/Dhaka'

STATIC_URL = 'static/'
STATIC_ROOT = os.path.join(BASE_DIR, "static")
MEDIA_ROOT = os.path.join(BASE_DIR, 'media')
MEDIA_URL = '/media/'

#8. inside the configuration urls.py real state folder:

from django.contrib import admin
from django.urls import path
from django.conf.urls.static import static
from django.conf import settings
from rest_framework_simplejwt.views import TokenRefreshView, TokenObtainPairView

urlpatterns = [
                  path('admin/', admin.site.urls),
                  path('api/token/', TokenObtainPairView.as_view(), name='token_obtain_pair'),
                  path('api/token/refresh/', TokenRefreshView.as_view(), name='token_refresh_view'),
              ] + static(settings.STATIC_URL, document_root=settings.STATIC_ROOT)


#9. super user create: python3 manage.py createsuperuser
