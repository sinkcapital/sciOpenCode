FROM python:3

WORKDIR /usr/src/app

RUN apt-get update && apt-get install -y unzip

#install google-chrome
RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add && \
    echo 'deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main' | tee /etc/apt/sources.list.d/google-chrome.list && \
    apt-get update && \
    apt-get install -y google-chrome-stable

#install selenium
RUN pip install selenium

#install ChromeDriver
ADD https://chromedriver.storage.googleapis.com/87.0.4280.20/chromedriver_linux64.zip /opt/chrome/
RUN cd /opt/chrome/ && \
    unzip chromedriver_linux64.zip

ENV PATH /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/opt/chrome

CMD [ "python", "./macSeleniumHeadless.py" ]

# docker build -t tmp-train .
# docker run -v `pwd`:/usr/src/app tmp-train
# docker run -i -t tmp-train bash
