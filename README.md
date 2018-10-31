__author__ = 'WP8Dev'
import os
import unittest
from selenium import webdriver
from appium import webdriver
from appium.webdriver.common.mobileby import MobileBy
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import time
#from PIL import Image
#import pytesseract


class ContactAppTestAppium(unittest.TestCase):
    DRIVER_EXE_PATH = "C:\swapnil\webdriver\chromedriver.exe"
    #userName = "swapnil142"
    #accessKey = "MnjcUTWkoEsgzqmwyRao"
    def setUp(self):
        desired_caps = {}
        self.desired_caps = {
            "build": "GenyMotion",
            "platformName":"Android",
            "deviceName": "192.168.116.102:5555",
            "app": "C:\\swapnil\\apk\\Test.apk",
            "noReset" : "true"
        }
        #self.driver = webdriver.Remote("http://" + self.userName + ":" + self.accessKey + "@hub-cloud.browserstack.com/wd/hub",self.desired_caps)
        self.driver = webdriver.Remote("http://localhost:4775/wd/hub", self.desired_caps)
        #self.driver = webdriver.Chrome(executable_path=self.DRIVER_EXE_PATH)
        self.tracelog("Log : Done with initial setup.")

    def tracelog(self, message):
        print(message)

    def test_signinform(self):
        time.sleep(15)
        print("******************1")
        print("******************2")
       # print(self.driver.page_source)
        print("******************")
        el3 = self.driver.find_element_by_xpath("//*[@content-desc='CONTINUE']")
        #time.sleep(5)
        el3.click()

        print("******************3")
        print(self.driver.page_source)
        print("******************")
        time.sleep(10)
        el4 = self.driver.find_element_by_xpath("//android.webkit.WebView[@content-desc=\"elux\"]/android.widget.EditText[1]")
        el4.send_keys("tetesttest@gmail.com")
        time.sleep(5)
        el5 = self.driver.find_element_by_xpath("//android.webkit.WebView[@content-desc=\"elux\"]/android.widget.EditText[2]")
        el5.send_keys("testdasdas")
        time.sleep(5)
        el6 = self.driver.find_element_by_xpath("//*[@content-desc='LOG IN' and @class='android.view.View']")
        el6.click()
        time.sleep(10)
    def tearDown(self):
        self.driver.quit()

if __name__ == '__main__':
    suite = unittest.TestLoader().loadTestsFromTestCase(ContactAppTestAppium)
    unittest.TextTestRunner(verbosity=2).run(suite)
