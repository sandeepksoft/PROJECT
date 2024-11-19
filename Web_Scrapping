import pandas
import numpy
import requests
import bs4

# extracting data from jiomart website using python 

# used link  : https://www.jiomart.com/c/electronics/mobiles-tablets/mobiles/32118
# bike wala ,imdb   ,zigwheels
r=requests.get("https://www.jiomart.com/c/electronics/mobiles-tablets/mobiles/32118")
print(r)   # <Response [200]>

soup=bs4.BeautifulSoup(r.content,'html.parser')
#soup=bs4.BeautifulSoup(r.content,'json.parser') # not working
#print(soup)

#names = soup.find_all('div',id='pdp_product_name')

# product name
names = soup.find_all('div',class_='plp-card-details-name line-clamp jm-body-xs jm-fc-primary-grey-80')
name=[]
for i in names[0:10]:
      #d=i.text # Works
      d=i.get_text() # Works
      name.append(d)
print(name)

# for i in name:
#     print(i,'\n')
# print(len(name))



#product price
prices = soup.find_all('span',class_='jm-heading-xxs jm-mb-xxs')
price=[]
for i in prices[0:10]:
      #d=i.text # Works
      d=i.get_text() # Works
      price.append(d)
print(price)

# product link  : anchor tag | link in href tag
links = soup.find_all('a',class_='plp-card-wrapper plp_product_list')
link=[]
for i in links[0:10]:
      d="https://www.jiomart.com"+i['href']
      # getting 'p/electronics/apple-iphone-13-128-gb-blue/590798555' this much onley so we appending  'https://www.jiomart.com/'
      link.append(d)
print(link)




# product image  || tried not working
#images = soup.find_all('img',class_='largeimage swiper-slide-img lazyautosizes lazyloaded')
# images = soup.find_all('img',class_='lazyautosizes ls-is-cached lazyloaded')
# #images = soup.find_all('img',class_='pswp__img')
# image=[]
# for i in images[0:12]:
#       di=i['src']
#       #d=i.div.img['src']  # IMAGE TAG KI CLASS LENAPPUDU
#       image.append(di)
# print(image)



# ---------------------- pandas--------------

# df =pandas.DataFrame()
# print(df)       # empty data frame

df =pandas.DataFrame()
data = {'Prduct Name' : name,  # if any error comes name.pandas.Series()  (or)   pandas.Series(names)
        'link':link ,'product Price':price}

df =pandas.DataFrame(data)    # got all data in table format
print(df)

# making a csv file with all data
df.to_csv('m.csv')







